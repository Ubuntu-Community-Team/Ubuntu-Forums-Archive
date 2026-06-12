---
title: "installation permissions quandry"
date: 2015-10-10
forum: Fedora/RedHat and derivatives
---

### Post by maclenin on 2015-10-10
Why would an application installed using sudo be so without execute permissions?

The application is located in /usr/bin/ - is owned by root - but with 644 permissions (rw r r).

Full disclosure: the application was installed on a centos7 server - however - it's linux, so I feel what you would say about one flavor could/should/would be generally true for the other....

Thanks for any thoughts or questions.

---

### Post by Sweet_Baby_Jamie on 2015-10-10
the command **sudo** is a Debian / Ubuntu thing.  CentOS is a Red Hat system.  It won't recognize that command.  You need to log in as root and change the application's permissions so that it can be used by a  user other than root.

---

### Post by maclenin on 2015-10-10
**Sweet_Baby_Jamie!**

Thanks for reply - I hear you re: the chmod / permissions bit - however, I am pretty certain sudo can be deployed within the [realm of CentOS]("https://wiki.centos.org/TipsAndTricks/BecomingRoot").... 

Perhaps, the sudoer in CentOS doesn't enjoy the same install powers that su provides....

Not certain....

---

### Post by Sweet_Baby_Jamie on 2015-10-10
**su** (super user) probably works

---

### Post by maclenin on 2015-10-10
I think chmod might save the day.

However, I am still curious to understand explicitly WHY, whichever installation method I used (sudo or su) - it did not apply "proper" / execute permissions....

Sudo (and its man page) is explicitly incorporated into the CentOS environment I am using - so it should, theoretically "act" the way it does in debian / ubuntu.... I will explore su, as well - however, I can't help but think something else lurks here....

---

### Post by oldos2er on 2015-10-10
Moved to Other OS Support, Fedora/Redhat and Derivatives.

---

### Post by maclenin on 2015-10-10
Thanks for the move.

...to follow-up on the above - just wondering whether the use of su vs sudo should impact an installation process in CentOS, and - as in my case - not bestow proper permissions to the application being installed....

---

### Post by oldos2er on 2015-10-10
Might I suggest you ask in [https://www.centos.org/forums/](https://www.centos.org/forums/) ? While we may have members familiar with Centos, it is not the focus of our support forums.

---

### Post by buzzingrobot on 2015-10-10
> **maclenin said:**
> **Sweet_Baby_Jamie!**

  I am pretty certain sudo can be deployed within the [realm of CentOS]("https://wiki.centos.org/TipsAndTricks/BecomingRoot").... 



Sure, you can sudo your fingers off in CentOS, Fedora and Red Hat.

During an install of any one of the three, you're given the option of giving administrative privileges to the user you create.  If you do, then that user is in sudoers and prefacing commands with "sudo" works as expected. sudoers can be edited (visudo) to extend that to anyone in the wheels group, with or without the password prompt.

---

### Post by maclenin on 2015-10-11
**oldos2r!**

I hear you - however, I have found the folks here provide peerless guidance on virtually all topics...it is my default first stop - and if I discover, elsewhere, a kernel which contradicts or enlightens, I'll be certain to post it back to the mother ship....

Speaking of which: **buzzingrobot!**

Thanks for the comments. That was my sense - however, might it be possible that su has greater power than sudo - even if a sudoer is set up with "ALL" access in /etc/sudoers?

Could an installation process error - i.e. trying to install without sudo - and then with sudo - ultimately install the application correctly - but assign permissions incorrectly?

This kind of behavior must have been observed in Debian / Ubuntu?

Just trying to cut to the possible source of the "strange" permissions assignment - and feel this might not be a centos-only scenario....

---

### Post by buzzingrobot on 2015-10-11
> **maclenin said:**
> 

...might it be possible that su has greater power than sudo ... 

They're intended to serve different, but related, purposes. And, both can be invoked in different ways. A voyage through their man pages will explain.

> Could an installation process error - i.e. trying to install without sudo - and then with sudo - ultimately install the application correctly - but assign permissions incorrectly?

Dunno.  I'd guess it depends on the install script and what it checks for. If the user lacks the permissions needed to write to a directory, though, then the write is not going to happen. It's certainly conceivable that a poorly written script might deposit files in the wrong places but never provide an indication that anything had gone wrong.

> This kind of behavior must have been observed in Debian / Ubuntu? 

AFIAK, su and sudo behave the same way across all distributions, They're core tools. Distributions differ in how they use those tools, whether or not they default to enabling a root user, how users are assigned to groups, what privileges group members have, who is in sudoers and how the default sudoers permissions are structured, etc.  

On your original question, if the permissions on some files after an install were incorrect, it's most likely because the install script set them incorrectly. It happens.  An official RPM shouldn't have that kind of problem, but a tar archive or a foreign or outdated RPM certainly could.

---

### Post by maclenin on 2015-10-12
Thanks for the additional comments.

In the interests of even fuller disclosure - I was trying to ultimately install awscli on the centos7 machine using the python pip utility:
```
admin@centos7 $ curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
admin@centos7 $ sudo python get-pip.py
admin@centos7 $ sudo pip install awscli
```
These are the related files and their permissions as they appeared in /usr/bin/, post-install. As I understand it, the bold entries should be executable (in comparing this install with a similar "sudo" ubuntu install):
```
-rw-r--r--  1 root root  814 Sep 30 21:26 **aws**
-rw-r--r--  1 root root 1411 Sep 30 21:26 **aws.cmd**
-rw-r--r--  1 root root 1135 Sep 30 21:26 **aws_completer**
-rw-r--r--  1 root root 1860 Sep 30 21:26 **aws_zsh_completer.sh**
-rwxr-xr-x  1 root root  232 Sep 30 21:22 easy_install
-rwxr-xr-x  1 root root  232 Sep 30 21:22 easy_install-2.7
-rw-r--r--  1 root root 1674 Sep 30 21:26** jp.py**
-rw-r--r--  1 root root 1842 Sep 30 21:26 jp.pyc
-rwxr-xr-x  1 root root  204 Sep 30 21:22 pip
-rwxr-xr-x  1 root root  204 Sep 30 21:22 pip2
-rwxr-xr-x  1 root root  204 Sep 30 21:22 pip2.7
-rwxr-xr-x  1 root root  214 Sep 30 21:26 pyrsa-decrypt
-rwxr-xr-x  1 root root  230 Sep 30 21:26 pyrsa-decrypt-bigfile
-rwxr-xr-x  1 root root  214 Sep 30 21:26 pyrsa-encrypt
-rwxr-xr-x  1 root root  230 Sep 30 21:26 pyrsa-encrypt-bigfile
-rwxr-xr-x  1 root root  212 Sep 30 21:26 pyrsa-keygen
-rwxr-xr-x  1 root root  235 Sep 30 21:26 pyrsa-priv2pub
-rwxr-xr-x  1 root root  208 Sep 30 21:26 pyrsa-sign
-rwxr-xr-x  1 root root  212 Sep 30 21:26 pyrsa-verify
-rw-r--r--  1 root root  593 Sep 30 21:26 **rst2html.py**
-rw-r--r--  1 root root  602 Sep 30 21:26 rst2html.pyc
-rw-r--r--  1 root root  790 Sep 30 21:26 **rst2latex.py**
-rw-r--r--  1 root root  732 Sep 30 21:26 rst2latex.pyc
-rw-r--r--  1 root root  599 Sep 30 21:26 **rst2man.py**
-rw-r--r--  1 root root  707 Sep 30 21:26 rst2man.pyc
-rw-r--r--  1 root root 1697 Sep 30 21:26 **rst2odt_prepstyles.py**
-rw-r--r--  1 root root 2038 Sep 30 21:26 rst2odt_prepstyles.pyc
-rw-r--r--  1 root root  763 Sep 30 21:26** rst2odt.py**
-rw-r--r--  1 root root  801 Sep 30 21:26 rst2odt.pyc
-rw-r--r--  1 root root  600 Sep 30 21:26 **rst2pseudoxml.py**
-rw-r--r--  1 root root  598 Sep 30 21:26 rst2pseudoxml.pyc
-rw-r--r--  1 root root  636 Sep 30 21:26** rst2s5.py**
-rw-r--r--  1 root root  647 Sep 30 21:26 rst2s5.pyc
-rw-r--r--  1 root root  785 Sep 30 21:26 **rst2xetex.py**
-rw-r--r--  1 root root  748 Sep 30 21:26 rst2xetex.pyc
-rw-r--r--  1 root root  601 Sep 30 21:26 **rst2xml.py**
-rw-r--r--  1 root root  610 Sep 30 21:26 rst2xml.pyc
-rw-r--r--  1 root root  669 Sep 30 21:26 **rstpep2html.py**
-rw-r--r--  1 root root  678 Sep 30 21:26 rstpep2html.pyc
-rwxr-xr-x  1 root root  211 Sep 30 21:22 wheel

```
Also, these files appear in /usr/local/bin/ on the ubuntu machine - and only in /usr/bin/ on centos7....

Thanks, again, for any insight.

---

### Post by maclenin on 2015-10-22
As I review, this could be a umask issue.... Sudoer installer / pip / python, root owner....

Will post as I untangle....

---

### Post by buzzingrobot on 2015-10-22
> **maclenin said:**
> ...
admin@centos7 $ sudo python get-pip.py
admin@centos7 $ sudo pip install awscii 

"sudo" is a way of allowing a user to temporarily acquire the privileges needed to accomplish a task he/she doesn't ordinarily have. Here, it's to alter the file system by installing software.  The'sudo' has no impact on the permissions, etc., of the files that are installed.
> 
These are the related files and their permissions as they appeared in /usr/bin/, post-install. As I understand it, the bold entries should be executable (in comparing this install with a similar "sudo" ubuntu install):
```
-rw-r--r--  1 root root  814 Sep 30 21:26 **aws**
-rw-r--r--  1 root root 1411 Sep 30 21:26 **aws.cmd**
-rw-r--r--  1 root root 1135 Sep 30 21:26 **aws_completer**
-rw-r--r--  1 root root 1860 Sep 30 21:26 **aws_zsh_completer.sh**
-rwxr-xr-x  1 root root  232 Sep 30 21:22 easy_install

```

None of the bold entries have had their execute bit enabled. They all seem to be python or shell scripts, which don't necessarily need to be executable because they're interpreted by python or the shell. E.g., Bash will accept the name of a file containing a script to read and interpret.

> Also, these files appear in /usr/local/bin/ on the ubuntu machine - and only in /usr/bin/ on centos7....


Not unusual for different distributions to put things in different places. (That's one reason why packages from "foreign" distributions and especially different packaging systems -- deb vs rpm --  usually don't install correctly:  The install scripts they contain want to put, and find, files in the "wrong" locations." )

---

### Post by maclenin on 2015-10-23
Thanks for the reply.

With regard to sudo / pip / umask, see [here]("http://stackoverflow.com/questions/11161776/pip-inconsistent-permissions-issues") and [here]("http://articles.slicehost.com/2010/7/17/umask-and-unusual-file-permissions-and-types").

The sudo umask setting is the "standard" [0022 / 022 / -rw-r--r--] on both the 12.04 and CentOS7 machines.

So, the CentOS 7 permissions could be correct - pending the execution of some sort of "configure" script - as you indicate....

However after installing / configuring the same on my 12.04 machine - the 12.04 /usr/**local**/bin/ snippet reads:
```
-rw**x**r-**x**r-**x**  1 root root  814 Sep 30 21:26 **aws**
-rw**x**r-**x**r-**x**  1 root root 1411 Sep 30 21:26 **aws.cmd**
-rw**x**r-**x**r-**x**  1 root root 1135 Sep 30 21:26 **aws_completer**
-rw**x**r-**x**r-**x**  1 root root 1860 Sep 30 21:26 **aws_zsh_completer.sh**
-rwxr-xr-x  1 root root  232 Sep 30 21:22 easy_install
```
Whether this permissions profile is "post-install" or "post-config" (or both), is not clear. I will run a "fresh" install on a 3rd machine (14.04) to investigate!

One other strange tidbit - I was not able check the version of **aws** on the CentOS machine using root via the command line (aws was not found), immediately post-install - until AFTER I had manually toggled the (rw)"x" switch (using chmod)....

More, anon!

Thanks for the help!

---

### Post by maclenin on 2015-10-24
So, a fresh 14.04 install using the following steps (which were also used to install the same on centos)...
```
user@xubuntu $ curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
user@xubuntu $ sudo python get-pip.py
user@xubuntu $ sudo pip install awscli
```
...yielded all with "x" - pre-configuraton (i.e. differently from the way they appear after the centos install - pre-configuration):
```
-rwxr-xr-x  1 root root  814 Oct 24 10:55 aws
-rwxr-xr-x  1 root root 1411 Oct 24 10:55 aws.cmd
-rwxr-xr-x  1 root root 1135 Oct 24 10:55 aws_completer
-rwxr-xr-x  1 root root 1860 Oct 24 10:55 aws_zsh_completer.sh
-rwxr-xr-x  1 root root  232 Oct 24 10:52 easy_install
-rwxr-xr-x  1 root root  232 Oct 24 10:52 easy_install-2.7
-rwxr-xr-x  1 root root 1674 Oct 24 10:55 jp.py
-rw-r--r--  1 root root 1842 Oct 24 10:55 jp.pyc
-rwxr-xr-x  1 root root  204 Oct 24 10:52 pip
-rwxr-xr-x  1 root root  204 Oct 24 10:52 pip2
-rwxr-xr-x  1 root root  204 Oct 24 10:52 pip2.7
```
Curiously - or not - the only files in /usr/local/bin/ on the 14.04 are files associated with this installation.

Perhaps, importantly, the following "remark" appeared in the terminal as the pip install began on the 14.04 machine (and probably did at the start of the centos install, as well):
```
The directory '/home/user/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled.
Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.

The directory '/home/user/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled.
check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.

Collecting pip

/tmp/tmpV_L20Q/pip.zip/pip/_vendor/requests/packages/urllib3/util/ssl_.py:90: InsecurePlatformWarning: A true SSLContext object is not available.
This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail.
For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning.
```

Thanks, again, for any thoughts.

---

