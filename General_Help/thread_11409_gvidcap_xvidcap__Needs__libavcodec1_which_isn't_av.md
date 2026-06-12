---
title: "gvidcap /xvidcap:  Needs  libavcodec1 which isn't available"
date: 2005-01-16
forum: General Help
---

### Post by ixus_123 on 2005-01-16
I'm trying to install **gvidcap**, the gnome frontend to xvidcap so that I can make screen capture movies, hopefully as an instructional / reference tool for future Linux converts.

When I try to install it via apt-get I'm told it needs  libavcodec1, which isn't available.  I have searched [http://apt-get.org/](http://apt-get.org/) for  libavcodec1 but with no results.

Is it part of something else?  I would have thought I had everything needed for video as I have installed mplayer with supporting codecs.

Can anyone help?

---

### Post by Daniel G. Taylor on 2005-01-16
Although completely unsupported you can add the Marillat third party repository to your repositories list and libavcodec1, 2, and cvs are available there.

[http://debian.video.free.fr/](http://debian.video.free.fr/)

I am using Ubuntu's Hoary (unstable) version and use the unstable repository. If you are using Warty it may be better to use the testing repository.

You can add the repository to /etc/apt/sources.list or under Settings -> Repositories under Synaptic.

[Edit] P.S. Remember to apt-get update or Reload in Synaptic to update your package index with the new packages!

[Edit 2] You might also be intersested in my [Key Status Monitoring](http://programmer-art.org/key-status) tool. I wrote it for some Inkscape tutorials I'm working on. Notice though that it requires the latest development versions of GTK+ and pygtk.

---

### Post by ixus_123 on 2005-01-16
Key Status Monitor look like a great adition for when I finally get this to work - thanks :)

--------------------------------------------------------------------

As for libavcodec I still can't get it.  I have added the sources for testing, unstable, source - everything( & updated) & it just wont find it.  I even tried from the terminal incase it was something wrong with synaptic.  This is what it said:

> The following packages have unmet dependencies:
  gvidcap: Depends: libavcodec1 (>= 1:0.4.8) but it is not going to be installedE: Broken packages
kieren@N10k:~ $ sudo apt-get remove libavcodec
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libavcodec 

Cording to the terminal its broken (?) I'm not sure how to move forward from here.

---

### Post by Daniel G. Taylor on 2005-01-16
It looks like you have a broken package on your system. I had this a few days ago with libgtksourceview, but was able to fix it pretty easily.

Open up Synaptic and in the lower left select Custom, then in the list above it select Broken to see which packages are broken. Which packages are there, and can you find out why they are broken? (You can try to update / re-install them to see why they are failing if that is the case)

---

### Post by ixus_123 on 2005-01-16
Not a thing is showing up when filtering for broken :[

---

### Post by Daniel G. Taylor on 2005-01-16
Ah, crap. Are you running Ubuntu on that iBook in your sig? Marillat is compiled for x86 and x86_64 (amd64) so the packages wouldn't show up.

On that same page I gave you above there is a link for unstable PPC packages (The G3 is a PowerPC chip unless I'm mistaken). You can try that link, but I only see libavcodec2 in there, not libavcodec1.

Worst case scenario I'd say you have to compile it yourself from sources and get the package to skip the dependencies check.

I guess this is good to know since I may be throwing Ubuntu's next release on my iBook G4.

---

### Post by ixus_123 on 2005-01-17
no I'm running it on a via motherboard with Nememiah 1ghz chip that is supposed to identify as 586 or 686 I think.  Most things seem to work ok bar Mencoder but I'll have to try again from source

---

### Post by macewan on 2005-03-06
[QUOTE=ixus_123]no I'm running it on a via motherboard with Nememiah 1ghz chip that is supposed to identify as 586 or 686 I think.  Most things seem to work ok bar Mencoder but I'll have to try again from source[/QUOTE]

had a bit of a time getting it working also but it does install - you may want to consider vnc2swf also

 [http://www.unixuser.org/~euske/vnc2swf/](http://www.unixuser.org/~euske/vnc2swf/)

---

