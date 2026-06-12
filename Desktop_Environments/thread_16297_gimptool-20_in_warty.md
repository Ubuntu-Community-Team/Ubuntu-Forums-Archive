---
title: "gimptool-20 in warty"
date: 2005-02-20
forum: Desktop Environments
---

### Post by jocsch on 2005-02-20
Hi,
can anybody help me to install libgimp2.0-dev?

I can't get it installed because it depends on libgtk2.0-dev which won't be installed.
As I am new to Ubuntu/debian I have no clue what the right approach may be to solve this issue. Or do I dont't have a chance to install libgimp. Which would be a killer because I can't install source plugin-ins into gimp.

Thanks,
 Markus

---

### Post by kassetra on 2005-02-20
Ok, first off, did you get your gimp from the standard warty repository or the backports repository?
 
 Also, what version of libgimp2.0-dev are you trying to install?

---

### Post by jocsch on 2005-02-20
>Ok, first off, did you get your gimp from the standard warty repository or the 
> backports repository?
Thanks for the anwser. This is a question I can' anwser. Where do I get the information about? I think it's the warty rep, cause I haven't alterened anything.
I once had a hoary seed but removed that to exclude these packages.

>Also, what version of libgimp2.0-dev are you trying to install?
2.0.2-3ubuntu5

The libgtk2.0-dev version, that wont be installed is: 2.4.10-1ubuntu1

Thanks,
 Markus

---

### Post by kassetra on 2005-02-20
[QUOTE=jocsch]Also, what version of libgimp2.0-dev are you trying to install?
 2.0.2-3ubuntu5
 
 The libgtk2.0-dev version, that wont be installed is: 2.4.10-1ubuntu1
 [/QUOTE]
 
 Ok... so here's what I'm thinking.
 Do you have these repositories:
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
 
 If you don't then that is most likely why it can't find/install libgtk2.0-dev

---

### Post by jocsch on 2005-02-20
Nope. Wasn't in my sources.list. I added them, did an apt-get update and tried again to install with 
apt-get install libgimp2.0-dev

But the same error appeared. Any other suggestions?

markus

---

### Post by kassetra on 2005-02-20
Yeah, try installing libgtk2.0-dev first, or try:
 
  ```
apt-get install libgtk2.0-dev libgimp2.0-dev
```

---

### Post by jocsch on 2005-02-20
Still not succesfull, here's the full dump: 

root@ubuntu:/etc/apt # apt-get install libgtk2.0-dev libgimp2.0-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.4.0-3) but it is not going to be installed
                 Depends: libx11-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
E: Broken packages

---

### Post by kassetra on 2005-02-20
Ok...  This will upgrade you to gimp 2.2, but this is how I installed the dev files like you want.
 
 Since I have all of these things installed just fine, I'll tell you how I did it.
 
 1. Open Synaptic: Computer->System Configuration->Synaptic Package Manager
 2. Add the warty backports repositories: Settings->Repositories->New
 URI: [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)
 Distribution: warty-backports
 Section(s): main universe restricted multiverse 
 then click Ok, and New again:
 URI: [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)
 Distribution: warty-extras
 Section(s): main universe restricted multiverse
 Click Ok.
 3. Click Reload
 4. Click Search, type in gimp & press enter
 5. Find libgimp2.0-dev in the list, and right click on it.
 6. Click on "Mark for Installation"
 7. If a popup appears asking "Mark additional required changes?" click on Mark (it should ask you this)
 8. Click Apply, and Apply again.
 
 That's how I did it.

---

### Post by jocsch on 2005-02-20
Sorry. Doesn't work  for me again. As soon as I right click and select "mark" I get  the libgtk2.0-dev dependency error again.

What's worth notice is that the packet version hasn't changed after adding the new repositories. It's still 2.0.2-3ubuntu5
If I then do a "packet->force version" and select the backported version, I see it for a very short time in the main window of the package manager, before the version jumps back to 2.0.2-3ubuntu5.

So I do not seem to be able to use the new repositories. Any idea why?

Thanks again,
 Markus

---

### Post by kassetra on 2005-02-20
[QUOTE=jocsch]Sorry. Doesn't work for me again. As soon as I right click and select "mark" I get the libgtk2.0-dev dependency error again.
 
 What's worth notice is that the packet version hasn't changed after adding the new repositories. It's still 2.0.2-3ubuntu5
 If I then do a "packet->force version" and select the backported version, I see it for a very short time in the main window of the package manager, before the version jumps back to 2.0.2-3ubuntu5.
 
 So I do not seem to be able to use the new repositories. Any idea why?
 
 Thanks again,
  Markus[/QUOTE]
 
 Oh oops, upgrade your gimp first.  my bad.

---

### Post by jocsch on 2005-02-21
doesn't work either. Same problem. The preselected version in package manager is gimp2.0.2-3ubuntu5

If I select "force version" and choose the ...warty-backports I see this version  for a very short time in the package explorer before it jumps back to gimp2.0.2-3ubuntu5

I can't install the backport version. Do you know the apt-get command for forcing the version? Maybe I can get an error text out of this.

Markus

---

### Post by Yukonjack on 2005-02-21
Could you post your sources.list.

---

### Post by jocsch on 2005-02-21
Here it is:

```

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ warty universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

# deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://backports.ubuntuforums.org/backports/ warty-backports main universe restricted multiverse

deb http://backports.ubuntuforums.org/backports/ warty-extras main universe restricted multiverse
```

---

### Post by Yukonjack on 2005-02-21
[QUOTE=jocsch]Here it is:

```

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ warty universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

# deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://backports.ubuntuforums.org/backports/ warty-backports main universe restricted multiverse

deb http://backports.ubuntuforums.org/backports/ warty-extras main universe restricted multiverse
```[/QUOTE]


You might want to try this and it should work for you. If you don't want 
nerim.net/debian-marillat just put # in front of it. Don't forget to update the list in apt or reload in synaptic after editing. 

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```

---

### Post by jocsch on 2005-02-21
I would really love to say that it helped. But it hadn't. I copied your file into my sources.list, did an apt-get update and a reload in the package manager.

After that I see the following line in the packagemanager:
             installed V.          latest V.
--------------------------------------------------------------------------
gimp  2.0.2-3ubuntu5    2.0.2-3ubuntu5    ....


Again, if I click on "force" I can see that there is a backport version. But I can't get this damn thing installed. It always jumps back to 2.0.2 before I can select "mark for installation"
I have really no clue why. This is a fresh installation of ubuntu. I hadn't installed anything else so far.

Any idea? Or how can I do this on the commandline. Maybe there is an error message I can post?

Thanks,
 Markus

---

### Post by kassetra on 2005-02-21
jocsch:  could you output the contents of /etc/apt/preferences for me?

---

### Post by jocsch on 2005-02-21
```
Package: *
Pin: release a=warty
Pin-Priority: 600

Package: *
Pin: release a=hoary
Pin-Priority: 10
```

Yup. I changed this also as I once tried to get a hoary package installed. Anything wrong with it?

---

### Post by kassetra on 2005-02-21
Only that you're telling synaptic that *NO MATTER WHAT* only use warty versions...

This happened to me at first as well!  If you temporarily move/rename that file you'll probably be able to upgrade just fine.

---

### Post by jocsch on 2005-02-22
thanks kassetra, it finally worked. Thanks for your patience. 
I for sure most read up about this prefences file.

Markus

---

### Post by kassetra on 2005-02-22
[QUOTE=jocsch]thanks kassetra, it finally worked. Thanks for your patience. 
I for sure most read up about this prefences file.

Markus[/QUOTE]

That file allows you to make versions of files, applications, etc. "sticky" so that they won't be upgraded... by "pinning" * to warty with a high pin number you were telling synaptic not to use anything but the warty versions.  That's why it would flip on you.

Let's say you relied upon java 1.4 -- you could pin the java version to just 1.4 so that no matter how many upgrades happen, it wouldn't upgrade the java.

Very useful in a corporate setting.  :)

---

