---
title: "Is tracd available on the repos"
date: 2009-06-23
forum: General Help
---

### Post by porchrat on 2009-06-23
Hi all

Which version of trac is that one on the repo. I don't really want to mess with apache2 if I can avoid it, but I would like to run trac.

The answer for me seems to be the standalone version of trac, tracd (unless someone can give me a reason not to use it). I have installed trac from the repos, but now I'm unsure as to whether or not it is tracd and whether or not it is going to need apache2. It never asked for it as a dependency, all it asked for was some python stuff, I imagine for some of the scripts it runs or that I would need to use to add functionality.

Also is there no way (other than putting it through apache) to get trac to authenticate through keys instead of passwords? I have read through the parts of the trac documentation (some fo the best I've seen for an open source project btw, well done to the guys working on trac) concerning authentication and it doesn't seem like I can, but I thought I should ask nonetheless.

SSL would also be desired as I might move things across for work that I obviously would like to make it as hard as possible for someone to take a look at that, again I'm not sure this is possible (although I have read about a SSLwrapper that could do the trick).

Links to guides would be much appreciated, I like to be able to see how others achieve things. It helps me understand a little better.

---

### Post by porchrat on 2009-06-24
OK I see you run tracd as a standalone server so it doesn't matter how the thing is installed.

I started tracd and tried to visit the server (I'm just using localhost at the moment to make a little simpler) and I got this:

```
Exception happened during processing of request from ('127.0.0.1', 49356)
Traceback (most recent call last):
  File "/usr/lib/python2.5/SocketServer.py", line 464, in process_request_thread
    self.finish_request(request, client_address)
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
    self.handle()
  File "/usr/lib/python2.5/BaseHTTPServer.py", line 316, in handle
    self.handle_one_request()
  File "/var/lib/python-support/python2.5/trac/web/wsgi.py", line 174, in handle_one_request
    gateway.run(self.server.application)
  File "/var/lib/python-support/python2.5/trac/web/wsgi.py", line 87, in run
    response = application(self.environ, self._start_response)
  File "/var/lib/python-support/python2.5/trac/web/standalone.py", line 88, in __call__
    return self.application(environ, start_response)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 363, in dispatch_request
    env_paths)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 456, in send_project_index
    req.hdf = HDFWrapper(loadpaths)
  File "/var/lib/python-support/python2.5/trac/web/clearsilver.py", line 135, in __init__
    raise TracError, "ClearSilver not installed (%s)" % e
TracError: ClearSilver not installed (/usr/lib/python2.5/site-packages/neo_cgi.so: undefined symbol: Py_InitModule4)
----------------------------------------
127.0.0.1 - - [24/Jun/2009 10:51:45] "GET /favicon.ico HTTP/1.1" 404 -
127.0.0.1 - - [24/Jun/2009 10:51:48] "GET /favicon.ico HTTP/1.1" 404 -

```

What does that mean?

Actually I think it is best if I start a new thread because this is moving a little off-topic and I have in fact answered my own question.

---

