---
title: "python exception when installing wxwidgets 2.8"
date: 2009-05-20
forum: General Help
---

### Post by Kruzty on 2009-05-20
I'm using synaptic to install wxWidgets 2.8 and get the following output:

> Selecting previously deselected package wx2.8-headers.
(Reading database ... 156180 files and directories currently installed.)
Unpacking wx2.8-headers (from .../wx2.8-headers_2.8.10.1-0_i386.deb) ...
Selecting previously deselected package libwxbase2.8-dev.
Unpacking libwxbase2.8-dev (from .../libwxbase2.8-dev_2.8.10.1-0_i386.deb) ...
Selecting previously deselected package libwxgtk2.8-dev.
Unpacking libwxgtk2.8-dev (from .../libwxgtk2.8-dev_2.8.10.1-0_i386.deb) ...
Selecting previously deselected package wx-common.
Unpacking wx-common (from .../wx-common_2.8.10.1-0_i386.deb) ...
Processing triggers for man-db ...
Setting up wx2.8-headers (2.8.10.1-0) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1476, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 894, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing wx2.8-headers (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libwxbase2.8-dev:
 libwxbase2.8-dev depends on wx2.8-headers (= 2.8.10.1-0); however:
  Package wx2.8-headers is not configured yet.
dpkg: error processing libwxbase2.8-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-dev:
 libwxgtk2.8-dev depends on wx2.8-headers (= 2.8.10.1-0); however:
  Package wx2.8-headers is not configured yet.
 libwxgtk2.8-dev depends on libwxbase2.8-dev (= 2.8.10.1-0); however:
  Package libwxbase2.8-dev is not configured yet.
dpkg: error processing libwxgtk2.8-dev (--configure):
 dependency problems - leaving unconfigured
Setting up wx-common (2.8.10.1-0) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 wx2.8-headers
 libwxbase2.8-dev
 libwxgtk2.8-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up wx2.8-headers (2.8.10.1-0) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1476, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 894, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing wx2.8-headers (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libwxbase2.8-dev:
 libwxbase2.8-dev depends on wx2.8-headers (= 2.8.10.1-0); however:
  Package wx2.8-headers is not configured yet.
dpkg: error processing libwxbase2.8-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-dev:
 libwxgtk2.8-dev depends on wx2.8-headers (= 2.8.10.1-0); however:
  Package wx2.8-headers is not configured yet.
 libwxgtk2.8-dev depends on libwxbase2.8-dev (= 2.8.10.1-0); however:
  Package libwxbase2.8-dev is not configured yet.
dpkg: error processing libwxgtk2.8-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wx2.8-headers
 libwxbase2.8-dev
 libwxgtk2.8-dev

A little help?

---

