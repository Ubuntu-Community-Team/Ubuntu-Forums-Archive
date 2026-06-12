---
title: "Skype and libqt4-core"
date: 2007-06-16
forum: Desktop Environments
---

### Post by John CCC on 2007-06-16
Hi, just installed Feisty.. lovin it.. Went to install Skype and got the following message: Error: > Dependency not satisfiable: libqt4-core 
I understand that I need that program for skype to work, but there appear to be about a dozen different versions available 
see: [http://packages.debian.org/unstable/libs/libqt4-core](http://packages.debian.org/unstable/libs/libqt4-core)

Apparently this was a dapper library 
[http://packages.ubuntu.com/dapper/libs/libqt4-core](http://packages.ubuntu.com/dapper/libs/libqt4-core)
and there are only three versions available from there.

I am not really sure which version to download.. and then a real noob question.. any ideas what I should do with it after I know which one to use?  lol
any help is appreciated.

---

### Post by trippinnik on 2007-06-16
What does your source.list look like?  It's the file that controls the places that your computer will search for new packages and updates.  You can  read it with the command gedit /etc/apt/sources.list  Another easy way to get Skype is to install Automatix2.  it's covered here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2) and the guide covers a lot of other stuff too.

---

### Post by John CCC on 2007-06-17
Hey thanks for the help...
I figured it out.  The ubuntu guide was brilliant. I didn't install the Automatix2 because of the warnings they gave in the guide.  ie: it can cause alot of issues.  However, I did find info on the Synaptic Package Manager... I followed the instructions there, and it gave me a ton of other apps to choose from, the one i needed was amongst them.  I added it, went back to Skype and re installed... bingo, I'm a up and runnin!
Thanks a ton.

---

### Post by Shlomir on 2007-10-19
I'm having similar problems..I tried to install the liqt4-core and still got an eroror for missing dependencies, is there a way to get them all installed at once, and can someone please post a HOW0TO I really want Skype to work

Thanks

---

### Post by martinr on 2008-03-03
Is there a way to install a working version of Skype on Ubuntu 6.06 LTS?
Skype 1.3 freezes up from time to time, which is un-acceptable. Skype 1.4 can't be installed on Dapper, but supposedly solves the problem.

The reason why synaptic can't install Skype 1.4 is:
> Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed 
> Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed 
> Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed 
> Depends: libqt4-core but it is not going to be installed 
> Depends: libqt4-gui but it is not going to be installed 
> Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed 

The Skype folks appearantly don't make an effort to support the Long Term Support Versions.
Have a look at:
[https://developer.skype.com/jira/browse/SCL-150](https://developer.skype.com/jira/browse/SCL-150)
[https://developer.skype.com/jira/browse/SCL-150]("https://developer.skype.com/jira/browse/SCL-150")

Should I just give up on Skype on Ubuntu 6.06?

---

### Post by vectorio on 2008-04-19
So how to install skype on Ubuntu 7.x? Somebody said he'd figured it out, but did not share his findings... I installed libqt4-core 4.2. something but the dependency error kept coming. Help is appreciated.

---

### Post by theredbaron on 2008-05-27
Not sure if anyone replied to this in another thread, but this is the one I found with google.

I found that my /etc/apt/sources.list was mostly commented out.  So I uncommented the lines:

<pre>
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
</pre>

and did apt-get update ; apt-get dist-upgrade

Then tried to install skype and it all worked fine.

Hope this is helpful to someone.

redbaron

---

