---
title: "Citrix and compiz fusion"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by MichaëlVD on 2007-09-16
Does anyone see the following problem: when using Citrix client to log in to my office server, I get disconnected whenever I do certain compiz things, such as rotating the cube.
I'm trying to narrow down the problem, but this is all the information I have right now. Thanks!

---

### Post by patchoro on 2007-09-16
I use a virtual Xp or Linux (VMware) to login to citrix. The virtual machine is located on one surface of the cube.  
This way the openGl doesn't interfere with the Citrix applications. It works like a charm.

---

### Post by MichaëlVD on 2007-09-16
That sounds like solid work around, but for me it would be just that: a work around. There is no other reason why I would want VMWare just for this purpose.

Have you tried logging in to the Citrix server without the virtual pc or vmware? And then, while the citrix window is active, start rotating the cube (CtrlAlt left/right)? I would like to know whether this problem is general, or just affects me because of a specific problem.

---

### Post by patchoro on 2007-09-16
> **MichaëlVD said:**
> 
Have you tried logging in to the Citrix server without the virtual pc or vmware? And then, while the citrix window is active, start rotating the cube (CtrlAlt left/right)? I would like to know whether this problem is general, or just affects me because of a specific problem.

Yes I have. the Citrix application just iconofies (is that an existing verb? ghehe )  when rotating the cube. I have no way of restoring that icon back to my screen.

I allready had Vmware running for other purposes so it was no hassle for me.

---

### Post by BanditManDan on 2007-09-17
I'm having exactly the same problem.  At one time I used Beryl instead of Compiz and remebered it working alright so I believe this problem is specific to Compiz.

---

### Post by kitofhawaii on 2007-11-30
Maybe it's a bit late but since I am assuming this is a common problem for Citrix/Compiz users (and this is the first google hit for "compiz citrix") I'll post my workarounds for others to find.  

The problem happens when you have a seamless-mode Citrix app maximized in one of your workspaces.  I'm sure this wreaks all sorts of havoc with OpenGL when you rotate the cube.  So there's two good workarounds that I use:

1. Where possible, don't use any Citrix apps maximized.  If they open off of Citrix maximized, click the restore button in the upper right hand side and you're off and running.  You can move the apps around to different workspaces without problem (minus some very minor cosmetic things while the ICA client catches up) without it bombing out.

2. If you really need that app maximized, (this bypasses the issue altogether) run a full Citrix desktop on one of your workspaces.  You can rotate fine and move the desktop to any workspace you want (just Ctrl-F2 when you're in the full desktop when you want to rotate.)

Hope this helps (experienced plenty of headaches with this one before I got it working, but at least I still have my hair :) .)

-kit

---

### Post by barrettboy on 2008-02-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156541](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156541) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				just fyi i raised a launchpad bug about this problem.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156541](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156541)

not sure how effective that will be, but i wasn't able to find out how to raise it with citrix.

cheers, Rob

---

### Post by Zodiachus on 2008-05-19
> **kitofhawaii said:**
> 
1. Where possible, don't use any Citrix apps maximized.  If they open off of Citrix maximized, click the restore button in the upper right hand side and you're off and running.  You can move the apps around to different workspaces without problem (minus some very minor cosmetic things while the ICA client catches up) without it bombing out.

Thanks for this! It worked like charm. Now I can finally start using Ubuntu extensively at work.

---

### Post by Caseyjp on 2008-07-08
From the citrix forums:
Re: Ubuntu 8.04 Compiz Citrix Presentation Server Client 10.6: small login mask
Posted: Jun 12, 2008 3:47 AM
Rating: Not Rated    Click to rate 	
  	Click to reply to this topic 	Reply

Thorsten,

We have seen this and suspect that it is due to a bug in Compiz.

When this error occurs, xwininfo shows that the window has been made Override Redirect and its X properties have been removed.

I hope this helps,

Phil 

Direct link:  [http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=103165&tstart=0]("http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=103165&tstart=0")

---

