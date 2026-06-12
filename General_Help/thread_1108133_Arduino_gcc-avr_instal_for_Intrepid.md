---
title: "Arduino gcc-avr instal for Intrepid?"
date: 2009-03-27
forum: General Help
---

### Post by bradcan on 2009-03-27
Hi All

I'm trying to install avr-gcc for Arduino programming on Ubuntu 8.10

Arduino installation instructions say there is a bug in the gcc-avr 4.3.0, this being the distribuiton for Intrepid.

The Arduino recommended procedure for installing gcc-avr on Intrepid is to install gcc-avr 4.3.2 form Jaunty packages!

I tried this but got a dependency error form Package Installer:
'Error: Dependency is not satisfiable: libc6'. However, according to Synaptic I have libc6 and libc6-dev installed!

It's not obvious from the error messages exactly what is missing, has anybody got any clues?

If I install avr-gcc 4.3.0 first I get conflicts with avr-libc! Is there, perhaps, a way to use avr-gcc_4.3.2-1_i366.deb to upgrade v4.3.0?

TIA

---

### Post by wrightjmf on 2009-04-02
Hi bradcan,

I'm just now trying this myself, so proceed with caution.

Make sure that you add both of the following sources to your /etc/apt/sources.list file and do a "sudo apt-get update" before you try to install the new gcc-avr and avr-libc packages:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

I then installed gcc-avr and avr-libc with the following line:

sudo apt-get install gcc-avr avr-libc

Beware though that this updates libc, so it's possible that it might break your system (although I haven't had any problem yet).

I hope that helps.

Jeremy

---

### Post by bradcan on 2009-04-06
Hi Jeremy

What is the update going to do, a full update to Jaunty?

Just so I know what I'm in for.

Thanks for the tip.

Brad

---

### Post by wrightjmf on 2009-04-07
Hi Brad,

You don't need to do a full upgrade to Jaunty to get the Arduino environment to work, you can just add the sources long enough to install the updated avr packages. If you want to do a dist-upgrade you can give it a shot, but I haven't tried it yet to tell you how/if it will work. When Jaunty is released on the 23rd, I'll probably do a full reinstall of my system. Right before that though I can try to upgrade my Intrepid install and then let you know what issues I run into trying to get the Arduino environment to work.

If you decide to only install the updated avr packages without the dist-upgrade, I would remove the apt entries for Jaunty when you're finished.

I hope that answers your question. If it doesn't, let me know.

By the way, I've been running Intrepid with the Jaunty avr/libc packages since my last post with no problems.

Jeremy

---

### Post by bradcan on 2009-04-11
Hi Jeremy,

Perhaps I'm being a bit dim! I'm not very familiar with apt-get (yet)!

The apt-get man page lists options "update", "upgrade" and "dist-upgrade".

If I understand your instructions and the man pages correctly, I put the additional lines in /etc/apt/sources.list and do "apt-get update".

Following this my system has "resynchronize(d) the package index files from their sources". I'm quoting the man pages.

So far nothing has changed in respect of actual installed packages, just made "information about new and updated packages available"?

Next the "sudo apt-get install gcc-avr avr-libc" installs the avr stuf, but now apt-get knows what the dependencies are, ie libc6?

So I just get gcc-avr, avr-libc installed and upgraded libc6. Correct?

One final question: If I wanted to roll back to the previous version of libc6 would  "apt-get remove gcc-avr avr-libc" do the trick?

Brad

---

### Post by wrightjmf on 2009-04-14
Brad,

That is correct. You add the sources to the /etc/apt/sources.list file and then do a "sudo apt-get update". You're also right in thinking that the update doesn't change your system, it just gets the list of available packages from the new source(s).

You can just do the installation the way you were thinking. Enter the

"sudo apt-get install gcc-avr avr-libc"

line and let apt upgrade any packages that it asks about (like libc6).

As far as rolling back to the earlier version, you should be able to do that, but just removing the avr packages will not roll back libc6. What I would NOT suggest though is removing libc6 with "sudo apt-get remove", followed by a "sudo apt-get install". Removing libc6 will take a lot of packages with it and (in my experience) will break your Ubuntu installation. 

First, I would comment/remove the Jaunty lines that you added to the sources.list file (if you haven't already done that) and then do a

"sudo apt-get update"

again. That will let your system know that the Jaunty packages are no longer available. After that, you can use the "sudo apt-get remove gcc-avr avr-libc" line to remove the avr packages. Once you've done that, use

"sudo apt-cache show libc6"

to show you what version(s) of libc6 are available for installation. On my system I looked at the "Version:" line, which showed "2.8~20080505-0ubuntu9". You may see several versions in the apt-cache output. I picked the "Version:" line in the second group down, which looked like it was the last libc6 version I had installed before I did the Jaunty libc6 upgrade. Once you have the version, insert the package and version information in the following command line:

"sudo apt-get install <pkgname>=<version>"

where you replace "<pkgname>" with "libc6" and "<version>" with the version string that you got from the output of apt-cache. So, in my case the line I entered was:

"sudo apt-get install libc6=2.8~20080505-0ubuntu9"

As always, use caution. I didn't have any problems when I tried it on my system, but I can't guarantee it will work for you.

Here are a couple of forum posts that are along the lines of what I'm talking about.

[http://ubuntuforums.org/showthread.php?t=478167](http://ubuntuforums.org/showthread.php?t=478167)

[http://ubuntuforums.org/showthread.php?t=45324](http://ubuntuforums.org/showthread.php?t=45324)

By the way, if you want to know the current version of libc6 that's installed, you should be able to use:

"/lib/libc.so.6"

I hope that helps. Let me know if you have any other questions.

Jeremy

---

