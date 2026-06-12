---
title: "TSclient &quot;cannot display this video mode&quot; error on remote Windows PC"
date: 2008-02-04
forum: Desktop Environments
---

### Post by Mr Potter on 2008-02-04
Not sure I'm posting this in the right place but here's the run down.  

Setup:

Client PC: Dell Latitude 4000, Intel PIII, 512 MB ram,  running Ubuntu 6.06 LTS, Gnome Lockdown Manager and TSclient 0.148.

Remote PC: Intel Core 2 Duo 2.13, Intel D946GZIS  MOBO with on board Intel X3000 video, 2gb ram, running Windows XP Pro SP2, Monitor is a Dell 17" 1704FPVt

The Problem:
The Dapper client PC connects/disconnects  to various Windows boxes no problem (Dell GX260,270,280,520,620) with a variety of different Dell LCDs.  However on machines with the above specs; 

-Client connects with out an issue
-It performs as expected.
-After going to Start>Disconnect or Log Off...the remote PC displays the Windows Log on box...again as expected.
-After the user logs in locally (sitting at the machine...not using TSclient) on the remote PC the "Cannot display this video mode" shows up on the monitor and we're dead in the water (requiring a reboot).
-After reboot the user can log on to the PC locally and every thing is  hunky dory?

I've got my suspicions that the RDP session is adjusting the remotes display settings down to the settings I have in TSclient  (1024 X 768 @16 bit color depth).  What I don't understand is why Windows is not releasing these settings once the session ends?  The problem does not occur until the user tries to log in.  I've been trying to find a setting in Windows or on Ubuntu that may be the cause of this, but I've pretty much exhausted Google in the last couple hours. All the other remote PC's I hit with this setup work with out complaint, so I'm leaning twords something being wrong in my Windows image for this PC model (we've got 26 of these, hence my diligence in finding a solution).  If anyone has any bright ideas please let me know. 

Thanks

---

