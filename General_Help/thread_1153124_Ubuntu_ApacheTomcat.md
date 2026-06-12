---
title: "Ubuntu Apache/Tomcat"
date: 2009-05-08
forum: General Help
---

### Post by johnjust on 2009-05-08
Hello all, not sure if this is the proper palce for this post, feel free to move it if needed...

I'm trying to get Apache and Tomcat installed, and have them connect so I don't have to specify the port number in the URL.

So, instead of

[http://localhost:8080/examples](http://localhost:8080/examples)

it should go to:

[http://localhost/examples](http://localhost/examples)

I've been following guides all around the net, Apache and Tomcat work perfect separately, but not together.

Here's what I've done so far:

1. Install Apache
2. Install Tomcat6
3. Download mod_jk.so, install in /usr/lib/apache2/modules/
4. Add to /etc/apache2/workers.properties

```

  # Define 1 real worker using ajp13
  worker.list=worker1
  # Set properties for worker1 (ajp13)
  worker.worker1.type=ajp13
  worker.worker1.host=localhost
  worker.worker1.port=8009

```

5. Add to http.conf:

```

ServerName localhost

  # Load mod_jk module
  # Update this path to match your modules location
  LoadModule    jk_module  /usr/lib/apache2/modules/mod_jk.so
  # Where to find workers.properties
  # Update this path to match your conf directory location (put workers.properties next to httpd.conf)
  JkWorkersFile /etc/apache2/workers.properties
  # Where to put jk shared memory
  # Update this path to match your local state directory or logs directory
  JkShmFile     /var/log/apache2/mod_jk.shm
  # Where to put jk logs
  # Update this path to match your logs directory location (put mod_jk.log next to access_log)
  JkLogFile     /var/log/apache2/mod_jk.log
  # Set the jk log level [debug/error/info]
  JkLogLevel    info
  # Select the timestamp log format
  JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
  # Send everything for context /examples to worker named worker1 (ajp13)
  JkMount  /examples/* worker1

```

6. Update connector ports in /etc/tomcat6/server.xml from "8080" to "80"
7. stop/restart apache
8. [http://localhost/examples](http://localhost/examples) doesn't work...

This server set-up is a little foreign to me, I usually always either work with a local XAMPP installation, or a host like Media Temple, so I'm not sure exactly where I went wrong.

If you need any output/answers from me, just leave a reply, I'll be checking back regularly.  As always, thanks for any help you can offer!

---

