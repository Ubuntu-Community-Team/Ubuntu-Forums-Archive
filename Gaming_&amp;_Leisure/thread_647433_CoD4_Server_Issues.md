---
title: "CoD4 Server Issues"
date: 2007-12-22
forum: Gaming &amp; Leisure
---

### Post by will808 on 2007-12-22
Hi,

I've posted this on a CoD4 forum but had no replies yet - I'm trying to setup a CoD4 dedicated server on Xubuntu 7.10 and am having a few problems getting the executables to execute.

I've followed the instructions and:

[1] Copied the contents of Setup/data/* into a directory on the server

[2] Unpacked the .bz2 containing the linux binaries as directed.

[3] Created a user for running the server and changed the owner and group of all the CoD4 files to that user.

When I run the "./cod4-lnxded" command to start the server, I get a message:

```

exec: 50: ./cod4_lnxded-bin: not found

```

The referenced file is present though. I've looked at line 50 in the cod4-lnxded file, and the few lines around it:

```

45  # Let's boogie!
46  if [ -x "${COD4_DATA_PATH}/cod4_lnxded-bin" ]
47  then
48	cd "${COD4_DATA_PATH}/"
49	exec "./cod4_lnxded-bin" $*
50  fi
51  echo "Couldn't run Call of Duty 4 server (cod4_lnxded-bin). Is 
52  COD4_DATA_PATH set?"
53  exit 1

```

I've also had a problem trying to run the Punkbuster executable - the commands don't result in any error messages, but the installer just doesn't run. I think there must be some issue which is causing the executables not to execute.

Can anybody make any suggestions? I think it's probably something very simple and stupid that I have done / not done...

---

### Post by will808 on 2007-12-23
Ok, I've found the problem - something to do with my cpu being an Athlon 64, as it runs fine on my intel laptop.

Does anyone know what needs to be done to make these binaries run on AMD64?

---

### Post by ram zu on 2007-12-29
Hi m8.

I'm using a amd64 to run my cod4 server with no problem.
Add a new user and created a cod4_server in that user home.
Put all the files in the dir (server zip and setup/data files) and run the same command.

Maybe you are pointing to some other dir or file.

---

### Post by Moustacha on 2007-12-30
are you running an amd64 version of a distro? if so you'll need to install the i386 compatibilities and/or libstdc++.so.5 (i think it's that one, previous CoDs needed it). Runs fine on a P4 and Athlon64 on i386 fedora 7

---

### Post by GOD-CGS- on 2008-01-11
> **will808 said:**
> Hi,

I've posted this on a CoD4 forum but had no replies yet - I'm trying to setup a CoD4 dedicated server on Xubuntu 7.10 and am having a few problems getting the executables to execute.

I've followed the instructions and:

[1] Copied the contents of Setup/data/* into a directory on the server

[2] Unpacked the .bz2 containing the linux binaries as directed.

[3] Created a user for running the server and changed the owner and group of all the CoD4 files to that user.

When I run the "./cod4-lnxded" command to start the server, I get a message:

```

exec: 50: ./cod4_lnxded-bin: not found

```

The referenced file is present though. I've looked at line 50 in the cod4-lnxded file, and the few lines around it:

```

45  # Let's boogie!
46  if [ -x "${COD4_DATA_PATH}/cod4_lnxded-bin" ]
47  then
48	cd "${COD4_DATA_PATH}/"
49	exec "./cod4_lnxded-bin" $*
50  fi
51  echo "Couldn't run Call of Duty 4 server (cod4_lnxded-bin). Is 
52  COD4_DATA_PATH set?"
53  exit 1

```

I've also had a problem trying to run the Punkbuster executable - the commands don't result in any error messages, but the installer just doesn't run. I think there must be some issue which is causing the executables not to execute.

Can anybody make any suggestions? I think it's probably something very simple and stupid that I have done / not done...

Same for me i've been banging my head against this all day
and it just doesnt want to play.:confused:

---

### Post by four2theizz0 on 2008-01-13
any updates?

---

### Post by kamasabi on 2008-01-15
I followed this guide here minus the punkbuster part:

[http://coding.lottor.net/index.php?topic=18](http://coding.lottor.net/index.php?topic=18)

if you're running the 64bit version of xubuntu, I have no idea, but I'm running the 32bit version of ubuntu 7.10 and it is running great.  Still trying to figure out all the configuration files and all, but otherwise, works good.

---

### Post by four2theizz0 on 2008-01-15
> **kamasabi said:**
> I followed this guide here minus the punkbuster part:

[http://coding.lottor.net/index.php?topic=18](http://coding.lottor.net/index.php?topic=18)

if you're running the 64bit version of xubuntu, I have no idea, but I'm running the 32bit version of ubuntu 7.10 and it is running great.  Still trying to figure out all the configuration files and all, but otherwise, works good.

hey man, thanks for the reply.  I managed to get it working, almost.  i still cant get the pbsetup.run to do anything...just wondering what happened when you did that.  

and another prob.  my friends can connect to the server now and I am using ModernRcon but when I try to connect, even just rhough a lan connection I get it timing out at "awaiting key code authorization" still.  I know it is something really small.  any suggestions?

Thanks again

also, I am running 32bit 7.10 Ubuntu.

---

### Post by four2theizz0 on 2008-01-16
this may be a dumb question, but am i not able to connect to my own serveR if im on the same ip?  like that would be why im getting the auth prob.
like is that known or something?  i would understand, but have just never heard it

---

### Post by danger89 on 2009-11-18
[http://www.markusbe.com/2009/09/about-running-32-bit-programs-on-64-bit-ubuntu-and-shared-libraries/](http://www.markusbe.com/2009/09/about-running-32-bit-programs-on-64-bit-ubuntu-and-shared-libraries/)

OR

[http://ubuntuforums.org/showthread.php?t=422767](http://ubuntuforums.org/showthread.php?t=422767)

---

