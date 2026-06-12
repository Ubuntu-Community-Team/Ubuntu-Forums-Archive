---
title: "Cannot install mysql gui tools"
date: 2008-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by syn4k on 2008-11-11
I have already downloaded and installed all of the dependencies...including mysql-client

I'm getting the error: configure: error: Could not find mysql_config script. Make sure the mysql client libraries are installed.

Here is my dep installer:
sudo apt-get -y install libcairomm-1.0-dev libpangomm-1.4-dev libgtkmm-2.4-dev libgtkmm-2.4-dbg libsigc++0c2 libsigc++-2.0-0c2a libsigc++-2.0-dev libsigc++-dev libglibmm-2.4-1c2a libglibmm-2.4-dbg libglibmm-2.4-dev libgtkmm-2.4-1c2a libgtkmm-2.4-dbg libgtkmm-2.4-dev libpangomm-1.4-1 libpangomm-1.4-dev mysql-client mysql-client-5.0

---

### Post by syn4k on 2008-11-11
Here is the complete installer I'm writing which you can use in reference to this thread...
```
# Build dependencies
sudo apt-get -y install libcairomm-1.0-dev libpangomm-1.4-dev libgtkmm-2.4-dev libgtkmm-2.4-dbg libsigc++0c2 libsigc++-2.0-0c2a libsigc++-2.0-dev libsigc++-dev libglibmm-2.4-1c2a libglibmm-2.4-dbg libglibmm-2.4-dev libgtkmm-2.4-1c2a libgtkmm-2.4-dbg libgtkmm-2.4-dev libpangomm-1.4-1 libpangomm-1.4-dev mysql-client mysql-client-5.0

# Get the mysql-gui-tools
http://dev.mysql.com/downloads/gui-tools
echo 'Downloading from mysql...'
wget -q http://dev.mysql.com/get/Downloads/MySQLGUITools/mysql-gui-tools-5.0r14.tar.gz/from/http://opensource.become.com/mysql/

# Decompress and install
tar -xf mysql-gui-tools-*
cd mysql-gui-tools-*/common/
sh autogen.sh
```

The reason I'm compiling this from source is because of this issue:
There is a known bug that seems to affect many Linux distributions where selecting a schema will actually crash the application. I'm working on compiling a version right now to fix this for myself. You can read more here:
[https://bugs.launchpad.net/ubuntu/+source/mysql-gui-tools/+bug/183446](https://bugs.launchpad.net/ubuntu/+source/mysql-gui-tools/+bug/183446)
[https://bugzilla.redhat.com/show_bug.cgi?id=266781](https://bugzilla.redhat.com/show_bug.cgi?id=266781)

Hopefully this helps somebody and maybe I can get some too!

---

### Post by syn4k on 2008-11-26
I upgraded to 8.10 and things seem to be working.

---

