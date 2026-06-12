---
title: "Certain forum stickied I've noticed need updating."
date: 2010-05-15
forum: Forum Feedback &amp; Help
---

### Post by kio_http on 2010-05-15
[FONT=Comic Sans MS][SIZE=4]**Case 1:**[/SIZE][/FONT]
**[FONT=Arial Black][SIZE=3][COLOR=Blue][Thread]("http://ubuntuforums.org/showthread.php?t=1006656")[/COLOR] in [COLOR=Blue] [Forum Feedback  & Help]("http://ubuntuforums.org/forumdisplay.php?f=48")[/COLOR][/SIZE][/FONT]**

[SIZE=2]_Issue:_[/SIZE]
The updating for this one is rather complex.
"[Why UbuntuForums.org uses vBulletin]("http://ubuntuforums.org/showthread.php?t=724506")"
This link leads to [another thread]("http://ubuntuforums.org/showthread.php?t=724506").
This thread in turn leads somewhere else suggesting that you can debate this fact in another thread.
**"If you wish to debate it, see [this  thread]("http://ubuntuforums.org/showthread.php?t=176622") and the threads it links to."**
That other thread is closed so no debating can be done there.

[SIZE=2]_Resolution:_[/SIZE]
I would suggest removing that last sentence I quoted.

[FONT=Comic Sans MS][SIZE=4]**Case 2:**[/SIZE][/FONT]
[FONT=Arial Black][SIZE=3][COLOR=Blue][Thread]("http://ubuntuforums.org/showthread.php?t=1011086")[/COLOR] in  [COLOR=Blue][Tutorials &  Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")[/COLOR][/SIZE][/FONT]

_Issue:_
The thread has been present for quite a while and has had no status update for a huge while. There is a mention of a request for volunteers but no way to apply for joining.

_Resolution:_
Either unsticky the thread if the project has collapsed or edit the post with a mention on how volunteers can apply.
[FONT=Comic Sans MS][SIZE=4]
**Case 3:**[/SIZE][/FONT] 
[FONT=Arial Black][SIZE=3][COLOR=Blue][Thread]("http://ubuntuforums.org/showthread.php?t=1422475")[/COLOR] in [COLOR=Blue][Absolute Beginner  Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")[/COLOR][/SIZE][/FONT]

_Issue:_
The thread is a rather good one but has the following issues. There is no mention about how to find the kernel type and version.  There is also no mention that unresolvable issues may indicate the need for submitting a bug report. Many known issues are unreported and affect our future releases because of this. 

I would also suggest improving the overall formatting and look of the thread,

_Resolution:_

[LIST]
[*]Mention bug reports and when they are not necessary
[*]Provide a link to the [COLOR=Blue][bug report thread]("http://ubuntuforums.org/showthread.php?t=1011078")[/COLOR]
[*]Mention how to find the kernel version (uname -a)
[*]Try to enrich the formatting
[/LIST]
**Case 4:**
[Thread]("http://ubuntuforums.org/showthread.php?t=1011078") in [Absolute Beginner  Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

[U]Issue:
[/U][SIZE=3][COLOR=Green]_**"-> Steps for filing a bug  report <-"**_[/COLOR][/SIZE]
The procedure in this section is no longer applicable to current releases of Lucid.
The relevant links does not link two important pages

[LIST]
[*]The bug triage wiki
[*]The Ubuntu bug squad
[*]The Ubuntu bug control
[/LIST]
_Resolution:_
1.
Update the procedure mentioning how to enable the apport service.
Edit the textfile
```
/etc/default/apport
```Changed the enabled value from 0 to 1
2.
Add links to the following pages

[LIST]
[*][COLOR=Blue][Bug triage]("https://wiki.ubuntu.com/Bugs/HowToTriage/")[/COLOR]
[*][COLOR=Blue][Helping with Bugs]("https://wiki.ubuntu.com/HelpingWithBugs/")[/COLOR]
[*][COLOR=Blue][Bug Squad]("https://wiki.ubuntu.com/BugSquad")[/COLOR]
[*][COLOR=Blue][Bug Control]("https://launchpad.net/%7Eubuntu-bugcontrol")[/COLOR]
[/LIST]

---

### Post by kio_http on 2010-05-15
Edit: forgot one
[FONT=Comic Sans MS][SIZE=4]**Case 5:**[/SIZE][/FONT]
[[FONT=Arial Black][SIZE=3]Thread[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1120414")[FONT=Arial Black][SIZE=3] in [**Virtualization  **]("http://ubuntuforums.org/forumdisplay.php?f=308")[/SIZE][/FONT]

_Issue:_
Title is Ubuntu 9.04

_Resolution:_
Update the thread for Lucid Lynx 10.04

---

### Post by cariboo on 2010-05-15
This didn't belong in the RC, as there is no personal issue to resolved

---

### Post by kio_http on 2010-05-15
> **cariboo907 said:**
> This didn't belong in the RC, as there is no personal issue to resolved

Ok... Got it.
RC for user related problems only.
Feedback for Forum and general problems/discussions

---

### Post by cariboo on 2010-05-15
We are aware of the sticky problem and have been discussing it it the staff sub-forum.

---

### Post by kio_http on 2010-05-15
> **cariboo907 said:**
> We are aware of the sticky problem and have been discussing it it the staff sub-forum.

Seems like I wasted my time.
Next time, kindly discuss only topics that need to be specifically hidden and perhaps unknown to other users or a specific group of users in the staff forum.

Also, actions speak better than words, the changes needed are not tremendous and can be fixed rather quickly.

---

### Post by bodhi.zazen on 2010-05-15
> **kio_http said:**
> Edit: forgot one
[FONT=Comic Sans MS][SIZE=4]**Case 5:**[/SIZE][/FONT]
[[FONT=Arial Black][SIZE=3]Thread[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1120414")[FONT=Arial Black][SIZE=3] in [**Virtualization  **]("http://ubuntuforums.org/forumdisplay.php?f=308")[/SIZE][/FONT]

_Issue:_
Title is Ubuntu 9.04

_Resolution:_
Update the thread for Lubid Lynx 10.04

You raise good points.

In terms of this thread, however, it still applies to 9.04.

I have not had the time to look into all the virtualization options with 10.04 yet.

To date I know -

Openvz - No longer supported .
LXC - In early development. 

[http://blog.bodhizazen.net/linux/lxc-linux-containers/](http://blog.bodhizazen.net/linux/lxc-linux-containers/)
[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

I would assume KVM / qemu and Virtualbox all work.

Have not tried VMWare, and there is now Player, server 1.x , server 2.x, and of course Workstation and ESXi.

If you would like to help, how about if you try VMWare (player, server 1.x, server 2.x, ESXi) and / or Virtualbox =)

I have asked for assistance in maintaining that particular sticky, but no takers ...

Otherwise, I will put it on my "to do list". Please keep  in mind we are all volunteers here and your feedback is appreciated.

---

### Post by kio_http on 2010-05-15
> **bodhi.zazen said:**
> 
Otherwise, I will put it on my "to do list". Please keep  in mind we are all volunteers here and your feedback is appreciated.

Thanks, I'll be sure to inform you if I do find an update method.

I have already tested out virtualbox and vmware (Only Player). I can confirm that both work perfectly on Lucid. As to the other vmware's I haven't tried them yet. 

If of any use, I have a thread in Tutorials and Tips for getting Windows running under vbox. I have been maintaining the thread and its completely compatible with lucid.

---

### Post by kio_http on 2010-05-16
> **bodhi.zazen said:**
> 
I have asked for assistance in maintaining that particular sticky, but no takers ...


I can suggest a possible way to maintain stickies.

Post a thread asking for volunteers to maintain and modify each thread I mentioned. Assign the tasks. When done, the users will post their updated version and forum staff can edit the stickies.

---

### Post by bodhi.zazen on 2010-05-16
> **kio_http said:**
> I can suggest a possible way to maintain stickies.

Post a thread asking for volunteers to maintain and modify each thread I mentioned. Assign the tasks. When done, the users will post their updated version and forum staff can edit the stickies.

I think we are at the step of recruiting volunteers.

With Virtualization I think I am going to fall back to officially supported packages, maintaining threads on un-supported options, such as XEN, VMWare, OpenVZ, etc is tedious and change with versions of the kernel, not necessarily Ubuntu versions.

Also these things really, IMO, should be maintained on the Wiki, the Ubuntu wiki is much more conducive to such efforts (larger scale projects with multiple potential authors) then the forums.

We would then link to the wiki pages.

I have started on a set of pages for LXC, for example, but it is early as I am still working my way through LXC and learning the ropes. If you look at the wiki page you will see others have helped, and, as you can see, it is much easier as multiple authors can not maintain a single thread on the forums.

[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

---

### Post by BslBryan on 2010-05-16
I offer to help in any way I can, bodhi.  If it does come down to volunteers, send me a PM. :)

---

