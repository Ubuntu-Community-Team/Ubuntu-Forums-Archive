---
title: "Request: Freevo 1.5.4"
date: 2005-10-17
forum: Deferred/Invalid Requests
---

### Post by dare2dreamer on 2005-10-17
I just read on the Freevo-Users mailing list that the new release has the long-awaited bugfix that will allow Freevo to work with python2.4

Any chance of packaging it up for Breezy?

---

### Post by chaumurky on 2005-10-23
It's not actually out yet, is it??
 
EDIT: Ahh, [so it is...]("http://prdownloads.sourceforge.net/freevo/freevo-1.5.4.tar.gz?download")

---

### Post by dare2dreamer on 2005-10-24
Yeah, for whatever reason, they haven't listed it on the webpage. I found out about it from the mailing lists.

---

### Post by chaumurky on 2005-10-24
I have it running from the sources (minus live TV but i havent really done much). One thing though, all those dependencies they're all built using setup.py scripts. Is there a way one can use 'checkinstall' with these scripts so I can remove them cleanly afterwards?

---

### Post by tigrez on 2005-10-25
It work, but you need to download the source code. It's python, don't need strange library, it is easy to do.

Anyway, I've some problem with my 4779 mame roms...

---

### Post by Xanadu on 2005-10-29
Hey guys

How the heck did you get mmpython to compile? Mine just complains.

Anyhow I've gotten Freevo 1.5.3 to work on Breezy. Updated debs are at [http://www.magnumip.co.za/~jason/freevo-breezy.tar.gz](http://www.magnumip.co.za/~jason/freevo-breezy.tar.gz)

Just install the other prereq's through apt or synaptic (python2.3, pygame and, er, that kind of stuff), unzip the archive, and ' sudo dpkg -i freevo-media_1.5.3-freevo1_all.deb freevo-1.5.3.breezy.deb'

It's quite a quick hack and some stuff doesn't seem to work for me, particularly the record server (although whether this is because of Breezy/Python probs or my own ineptitude I'm not sure).

My server is a little short on bandwidth so if anyone finds this useful and would like to mirror it please don't be shy.

---

### Post by chaumurky on 2005-10-30
That's strange. What errors did you get with your mmpython compile? I had no problems.

---

### Post by Xanadu on 2005-10-30
[QUOTE=chaumurky]That's strange. What errors did you get with your mmpython compile? I had no problems.[/QUOTE]

Hi Chaumurky

My 1.5.3 version DOES work with recordserver (just had to configure it right, doh!). But in the interest of science and progress, I'll carry on with the attempt to get 1.5.4 working too ;)

Error is below:
sudo python setup.py install
Password:
running install
running build
running build_py
running build_ext
Traceback (most recent call last):
  File "setup.py", line 54, in ?
    ext_modules = extensions
  File "/usr/lib/python2.4/distutils/core.py", line 149, in setup
    dist.run_commands()
  File "/usr/lib/python2.4/distutils/dist.py", line 946, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/install.py", line 506, in run
    self.run_command('build')
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/build.py", line 112, in run
    self.run_command(cmd_name)
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/build_ext.py", line 254, in run
    customize_compiler(self.compiler)
  File "/usr/lib/python2.4/distutils/sysconfig.py", line 161, in customize_compiler
    cpp = cc + " -E"           # not always
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

---

### Post by jdong on 2005-11-11
EXTRAS -- deferred.

---

### Post by rbaalen on 2005-11-12
Hi,

Recently i installed Ubuntu and now im trying to install freevo. Using get-apt doesn't seem to work, see error bellow:


The following packages have unmet dependencies:
  freevo: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed
E: Broken packages

python setup.py install' doesn't work either, see the error below 

checking for mmpython...   not found
please download it from [http://www.sf.net/projects/mmpython](http://www.sf.net/projects/mmpython) and install it.

But downloading and installing mmpython does'nt work, due to the following error:

running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

Could you tell me how you mastered the install ?? I have googled arround but nothing sofar.

Greetz,

Rob

---

### Post by StianH on 2005-12-10
rbaalen: Try installing python-dev (sudo apt-get install python-dev)

---

### Post by stimulator on 2005-12-24
Hey Y'all,

I've got freevo almost working and I am asking for help becuase I am at a loss. Also I am a newbie to the wrold of Linux.

So I can schedule a recording with video but not with sound. I've combed the internet for information but alas here I am. I can hear the audio on the speakers once the recording starts but when I play back, nothing. I installed the alsa mixer gui and this is what it looks like. I want to know if this is configured wrong.

[IMG]http://submediatv.com/freevo/alsa_mixer.png[/IMG]

thanks

---

### Post by el_pombo on 2006-01-18
Hi...
If you have this problem:

The following packages have unmet dependencies:
freevo: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed
E: Broken packages

python setup.py install' doesn't work either, see the error below 

Try installing the following packages: python2.4 and python2.4-dev (sudo apt-get install python2.4 python2.4-dev), then type in the shell: "sudo python2.4 setup.py install"...
maybe this will fix your problem.

Good luck.

---

### Post by chaumurky on 2006-01-27
I just added the repository:

deb [http://sitadelle.ath.cx/ubuntu-extras]("http://sitadelle.ath.cx/ubuntu-extras") breezy extras 


And it installed flawlessly. :-)

---

### Post by chadk on 2006-07-30
Any update for Dapper?

---

