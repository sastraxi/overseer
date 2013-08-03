Everything is either an app or a database.
Each category has an app part and a database part,
and can be shared across as many servers as you'd like

META:
 App:
  - run scripts on database every night
  - log (stats + error) viewer
  - continuous integration (to staging)
 Data:
  - version control
  - stats ("data about data")
  - access logs
  - error logs

APP:
 App:
  - actual application
 Data:
  - temporary caches
  - distributed memory to be written to db (e.g. redis)

STAGING:
 App:
  - actual application
 Data:
  - example/test database

DEVEL:
 App:
  - any processes the developers wish to run, e.g.
    long-running tests, mail servers, IRC...
 Data:
  - devel database (periodically cloned from the production db)

DATA:
 Data:
  - production DB
  - distributed DB 

=========================
unrelated
- DB migration scripts folder in depot/migrations/[servername]
- trigger on commits with a message @migrate
- triggered script then executes the script, if errored out emails the committer,
  if successful moves it to migrations/executed/devel.lyricfind.com/
- ma


=========================
unrelated
- jenkins should distribute WARs and a script on each server
  should keep track of what SVN revision is current and
  what SVN revision is incoming:
  - jenkins does scp to "/root/incoming/r24126/api_service.war"
  - update_api.sh checks for a new war and tells you which
    revision is currently running by comparing md5sum with
    incoming/*/api_service.war

  