---
title: "windows manager &quot;compiz&quot; won't register configuration tool"
date: 2009-03-29
forum: General Help
---

### Post by spodumene on 2009-03-29
Hi, I've only been using Ubuntu for a couple of days and I recently re-installed Gnome but my desktop seems to be missing some applications. I get an error message that looks like this when I go to System -> preferences -> windows:

windows manager "compiz" has not registered configuration tool.
  
So I decided to install ccsm but I get an error for 5 files:

Errors were encountered while processing:
 libwmf0.2-7
 libmagick10
 rss-glx
 ghostscript
 ghostscript-x

This is what the entire message looks like in the terminal:

jf@grifbuntu:~$ sudo aptitude install compizconfig-settings-manager
[sudo] password for jf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  ghostscript ghostscript-x gsfonts libmagick10 libwmf0.2-7 rss-glx 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up gsfonts (1:8.11+urwcyr1.0.7~pre43-2) ...
(Re-)registering PostScript fonts...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing gsfonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ghostscript:
 ghostscript depends on gsfonts (>= 6.0-1); however:
  Package gsfonts is not configured yet.
dpkg: error processing ghostscript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-x:
 ghostscript-x depends on ghostscript (>= 8.63); however:
  Package ghostscript is not configured yet.
dpkg: error processing ghostscript-x (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwmf0.2-7:
 libwmf0.2-7 depends on gsfonts; however:
  Package gsfonts is not configured yet.
dpkg: error processing libwmf0.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmagick10:
 libmagick10 depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing libmagick10 (--configure):
 dependency problems - leavinNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                                                                                               No apport report written because MaxReports is reached already
                      g unconfigured
dpkg: dependency problems prevent configuration of rss-glx:
 rss-glx depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing rss-glx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gsfonts
 ghostscript
 ghostscript-x
 libwmf0.2-7
 libmagick10
 rss-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libwmf0.2-7:
 libwmf0.2-7 depends on gsfonts; however:
  Package gsfonts is not configured yet.
dpkg: error processing libwmf0.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmagick10:
 libmagick10 depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Package libwmf0.2-7 is not configured yet.
dpkg: error processing libmagick10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rss-glx:
 rss-glx depends on libmagick10; however:
  Package libmagick10 is not configured yet.
dpkg: error processing rss-glx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript:
 ghostscript depends on gsfonts (>= 6.0-1); however:
  Package gsfonts is not configured yet.
dpkg: error processing ghostscript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-x:
 ghostscript-x depends on ghostscript (>= 8.63); however:
  Package ghostscript is not configured yet.
dpkg: error processing ghostscript-x (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwmf0.2-7
 libmagick10
 rss-glx
 ghostscript
 ghostscript-x
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


Any idea how I could fix this issue??

Cheers

---

### Post by sailthesea on 2009-03-29
It looks like some ccm packages weren't properly installed try reinstalling or I'm sure there's some God-like command for terminal that will find and fix partials
 Edit: Which may be 

sudo defoma-reconfigure -f 
 I think that's what the error console is giving here:

E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status
 You should have to enter your password
Don't do this if you don't trust me Be VERY careful what you type in Terminal (I should know I killed one install with a typo!)

 Let me know what happens cos I'm trying desktops out myself and am a bit in the dark myself
 By the way Welcome:)

---

### Post by spodumene on 2009-03-30
Hi, thanks for the response. I typed in 

sudo defoma-reconfigure -f 

and was able to fix the problem. I am still trying to figure how to properly register the configuration tool in Compiz so my desktop works normally again

Cheers

---

