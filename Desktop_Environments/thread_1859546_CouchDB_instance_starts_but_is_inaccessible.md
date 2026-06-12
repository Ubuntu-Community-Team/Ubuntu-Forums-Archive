---
title: "CouchDB instance starts but is inaccessible"
date: 2011-10-14
forum: Desktop Environments
---

### Post by bogdanbiv on 2011-10-14
Accessing my local CouchDB at [http://127.0.0.1:5984/](http://127.0.0.1:5984/) gives a 404. I've checked and the binding address and port are still 127.0.0.1 and 5984.
CouchDB starts with message OK, but an error appears in the logfile:

```
[Fri, 14 Oct 2011 03:51:28 GMT] [error] [<0.87.0>] {error_report,<0.32.0>,
              {<0.87.0>,supervisor_report,
               [{supervisor,{local,couch_secondary_**********},
                {errorContext,start_error},
                {reason,{'EXIT',{{badmatch,{error,einval}},
                                 [{mochiweb_socket_server,parse_options,2},
                                  {mochiweb_socket_server,start,1},
                                  {couch_httpd,start_link,0},
                                  {supervisor,do_start_child,2},
                                  {supervisor,start_children,3},
                                  {supervisor,init_children,2},
                                  {gen_server,init_it,6},
                                  {proc_lib,init_p_do_apply,3}]}}},
                {offender,[{pid,undefined},
                           {name,httpd},
                           {mfa,{couch_httpd,start_link,[]}},
                           {restart_type,permanent},
                           {shutdown,1000},
                           {child_type,worker}]}]}}
```
Also see my pastebin [http://pastebin.com/TwhLU8aG]("http://pastebin.com/TwhLU8aG") for more wierd looking error messages.

I cant make any sense of it, could someone translate that error in Simple English?

Also, here is a list of processes that contain couchdb:

```
bogdanbiv@desktop07:~$ ps aux | grep couch
root      3793  0.0  0.0 128156  1752 pts/0    S+   06:57   0:00 sudo tail -f /var/log/couchdb/couch.log
root      3794  0.0  0.0  89904   584 pts/0    S+   06:57   0:00 tail -f /var/log/couchdb/couch.log
couchdb   4510  0.0  0.0   4220   688 pts/3    S    07:40   0:00 /bin/sh -e /usr/bin/couchdb -a /etc/couchdb/default.ini -a /etc/couchdb/local.ini -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
couchdb   4524  0.0  0.0   4220   348 pts/3    S    07:40   0:00 /bin/sh -e /usr/bin/couchdb -a /etc/couchdb/default.ini -a /etc/couchdb/local.ini -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
couchdb   4525  0.6  0.2  80160 13132 pts/3    Sl   07:40   0:00 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -A 4 -- -root /usr/lib/erlang -progname erl -- -home /var/lib/couchdb -- -noshell -noinput -sasl errlog_type error -couch_ini /etc/couchdb/default.ini /etc/couchdb/local.ini /etc/couchdb/default.ini /etc/couchdb/local.ini -s couch -pidfile /var/run/couchdb/couchdb.pid -heart
couchdb   4540  0.0  0.0   3984   324 ?        Ss   07:40   0:00 heart -pid 4525 -ht 11
1000      4549  0.0  0.0  92172  1060 pts/3    S+   07:41   0:00 grep --color=auto couch
```

I've tried to stop the service with init.d scripts, but it didn't work so I've killed all processes containing couchdb (pkill couchdb) and kill $pid for the process containing /usr/lib/erlang/erts-5.7.4/bin/beam.smp.


So I've started it again
bogdanbiv@desktop07:~$ sudo /etc/init.d/couchdb start
 * Starting database server couchdb            [ OK ]

And now the same set of processes are up:
```
couchdb   4667  0.0  0.0   4220   684 pts/3    S    08:01   0:00 /bin/sh -e /usr/bin/couchdb -a /etc/couchdb/default.ini -a /etc/couchdb/local.ini -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
couchdb   4682  0.0  0.0   4220   348 pts/3    S    08:01   0:00 /bin/sh -e /usr/bin/couchdb -a /etc/couchdb/default.ini -a /etc/couchdb/local.ini -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
couchdb   4683  0.1  0.2  80672 13332 pts/3    Sl   08:01   0:00 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -A 4 -- -root /usr/lib/erlang -progname erl -- -home /var/lib/couchdb -- -noshell -noinput -sasl errlog_type error -couch_ini /etc/couchdb/default.ini /etc/couchdb/local.ini /etc/couchdb/default.ini /etc/couchdb/local.ini -s couch -pidfile /var/run/couchdb/couchdb.pid -heart
couchdb   4697  0.0  0.0   3984   328 ?        Ss   08:01   0:00 heart -pid 4683 -ht 11
```

Stopping the processes works:
bogdanbiv@desktop07:~$ sudo /etc/init.d/couchdb stop
[sudo] password for bogdanbiv: 
 * Stopping database server couchdb            [ OK ]

bogdanbiv@desktop07:~$ ps aux | grep couch
root      3793  0.0  0.0 128156  1752 pts/0    S+   06:57   0:00 sudo tail -f /var/log/couchdb/couch.log
root      3794  0.0  0.0  89904   584 pts/0    S+   06:57   0:00 tail -f /var/log/couchdb/couch.log
1000      4632  0.0  0.0  92168  1064 pts/3    R+   08:00   0:00 grep --color=auto couch

**UPDATE**:
I've done an sudo aptitude purge couchdb and then sudo aptitude install couchdb. Aptitude has started couchdb itself and here is the log :
```
[Sat, 15 Oct 2011 06:01:05 GMT] [error] [<0.87.0>] {error_report,<0.32.0>,
              {<0.87.0>,supervisor_report,
               [{supervisor,{local,couch_secondary_**********},
                {errorContext,start_error},
                {reason,{'EXIT',{{badmatch,{error,einval}},
                                 [{mochiweb_socket_server,parse_options,2},
                                  {mochiweb_socket_server,start,1},
                                  {couch_httpd,start_link,0},
                                  {supervisor,do_start_child,2},
                                  {supervisor,start_children,3},
                                  {supervisor,init_children,2},
                                  {gen_server,init_it,6},
                                  {proc_lib,init_p_do_apply,3}]}}},
                {offender,[{pid,undefined},
                           {name,httpd},
                           {mfa,{couch_httpd,start_link,[]}},
                           {restart_type,permanent},
                           {shutdown,1000},
                           {child_type,worker}]}]}}

[Sat, 15 Oct 2011 06:01:05 GMT] [error] [<0.79.0>] {error_report,<0.32.0>,
    {<0.79.0>,supervisor_report,
     [{supervisor,{local,couch_server_sup}},
      {errorContext,start_error},
      {reason,shutdown},
      {offender,
          [{pid,undefined},
           {name,couch_secondary_**********,
           {mfa,{couch_server_sup,start_secondary_services,[]}},
           {restart_type,permanent},
           {shutdown,infinity},
           {child_type,supervisor}]}]}}
```

Aptitude output:
```
Setting up couchdb (1.0.1-0ubuntu15) ...
 * Starting database server couchdb               [ OK ]
```


**UPDATE**: After a fresh install of Kubuntu 11.10, Couchdb starts correctly.

---

