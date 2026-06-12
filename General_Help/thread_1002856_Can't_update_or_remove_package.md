---
title: "Can't update or remove package"
date: 2008-12-05
forum: General Help
---

### Post by supradave on 2008-12-05
I'm trying to run an update on my packages and it fails telling me I have a broken package.  I run apt-get -f install and get this:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  opencryptoki
The following packages will be upgraded:
  opencryptoki
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/47.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package opencryptoki.
(Reading database ... 138382 files and directories currently installed.)
Preparing to replace opencryptoki 2.2.6+dfsg-1 (using .../opencryptoki_2.2.6+dfsg-1ubuntu1_i386.deb) ...
Stopping PKCS#11 slot daemon: invoke-rc.d: initscript opencryptoki, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping PKCS#11 slot daemon: invoke-rc.d: initscript opencryptoki, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/opencryptoki_2.2.6+dfsg-1ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting PKCS#11 slot daemon: pkcsslotd.
Errors were encountered while processing:
 /var/cache/apt/archives/opencryptoki_2.2.6+dfsg-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've trying to purge this and its dependency and still get a very similar message.  Does this package go with ecryptfs?

Thanks for the help,
Dave

---

### Post by robobot on 2008-12-05
I'm having similar problems but with a different package.
Here's my thread:
[http://ubuntuforums.org/showthread.php?t=1002067]("http://ubuntuforums.org/showthread.php?t=1002067")
There's no solution there yet, but it may be useful later.

---

### Post by Kevbert on 2008-12-05
Try this, substituting your relevant package list:
> Try the same as here: [https://answers.launchpad.net/ubuntu/+question/2591](https://answers.launchpad.net/ubuntu/+question/2591)

Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo -i

give your user password when requested, you don't see nothing when you type it, then press enter.

Then type a command similar to this echo -en '\n' | sudo tee -a /var/lib/dpkg/info/gxine.list
substitute the path and the .list file

For example:
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/thunar.list
Taken from [[COLOR="Red"]here[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/40321").

---

### Post by supradave on 2008-12-05
No, that's not it.

---

### Post by jxx66 on 2008-12-06
Hi,

i had the same issue. Problem seems to be that the stop function in the start script does work. In my setup the service was not started at all, so I just inserted a "exit 0" in the beginning of the script and was able to remove the package.

Hope that helps

Jan

---

### Post by supradave on 2008-12-08
Thanks for this.  I had to put the exit into the /var/lib/dpkg/info/file.prerm script after I killed the processes that were running.

---

### Post by HvRooyen on 2008-12-09
Thanks Jan. 
For those who need more info:
After checking that pkcsslotd was not running,  
sudo gedit /etc/init.d/opencryptoki to insert exit 0 as described above, re-ran package manager. Problem solved.

Henk

---

