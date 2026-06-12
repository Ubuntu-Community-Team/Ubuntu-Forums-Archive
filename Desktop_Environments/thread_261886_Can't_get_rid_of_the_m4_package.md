---
title: "Can't get rid of the m4 package"
date: 2006-09-20
forum: Desktop Environments
---

### Post by 3str on 2006-09-20
I installed the m4 package due to some dependency request. Now evey time the apt-get or dpkg runs, it gives a error message like this:

Configuring m4 (1.4.4-1) ...
install-info: unrecognized option `--description=The GNU m4 macro preprocessor.'        Try `install-info --help' for a complete list of options.
dpkg&#65306;error occured when processing m4 (--configure):
 subprocess·post-installation script·returned with error code·1
error occured when processing the following package&#65306;
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried apt-get install -f, and dpkg -r --force-all m4, but still no use.

What can I do?

---

