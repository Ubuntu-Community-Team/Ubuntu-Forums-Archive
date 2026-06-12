---
title: "urgent problem"
date: 2009-03-03
forum: General Help
---

### Post by flylehe on 2009-03-03
Hi,
I am having trouble with opening my folder explorer, synaptic package manager and update manager and some other applications:

When I click synaptic package manager and update manager , it always repeats saying my password for root is not correct. 

When I click Places -> Computer, I got error like "An error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly" and "GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Server ping error: IDL: omg.org/CORBA/COMM_FAILURE:1.0)". 

I googled and found this page [http://ubuntu-virginia.ubuntuforums....d.php?t=666845](http://ubuntu-virginia.ubuntuforums....d.php?t=666845) and I realized that I mananually clean up /tmp. So I tried what one suggested in the post that "sudo rm -rf /tmp && sudo mkdir /tmp && sudo mkdir /tmp/.X11-unix && sudo mkdir /tmp/.ICE-unix". But things still remain and now even now error message comes out.

How could I fix it? Thanks! 
           


Update:
I just restarted Ubuntu and this is the error I get when I try but fail to login:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

how to do "logging in with one of the failsafe sessions"?

---

