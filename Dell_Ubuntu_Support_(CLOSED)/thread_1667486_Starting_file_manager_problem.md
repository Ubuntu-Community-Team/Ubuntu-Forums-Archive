---
title: "Starting file manager problem"
date: 2011-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paulholbrook on 2011-01-14
Starting file manager problem 

--------------------------------------------------------------------------------

Background: 3 months ago I bought a Dell desktop computer with Windows and then installed Ubuntu 10/10 with dual boot. I normally use Ubuntu but ran into a mojor problem yesterday because Ubuntu locks up on me.

I boot up Ubuntu and get it up. It works fine for 60 seconds and then across the bottom of the screen, I see "Starting file manager." This message then quickly repeats across the bottom of the screen like it is starting this program mutliple times. Within a couple seconds the cursor shows the BUSY circle and I can't perform any commands. The only way to get out is to push the start button on the PC and I get the screen to Shutdown, Restart, etc.

In the 1st minute after startup, I can go into PLACES and it looks like Ubuntu One is not active. I have been using U1 for the past couple weeks for backing up the Documents and Pictures folders. They had the U1 symbols on them for Syncronizing. Those symbols are not there now so I assume U1 has stopped working.

Yesterday, I applied some maintenace which finished OK; I dragged a copy of the Documents folder to a flash drive for backup (I assume that is still allowed with U1 active). 

I had been trying to get U1 going on my laptop (Ubuntu 10/10)to synchronize files on the desktop and laptop but it always says it is "disconnected" and I couldn't get it started. When I went into the U1 dashboard on the laptop, it would show U1 had 1.5 GB used and would show the Documents and Pictures folders as belonging to U1. Yesterday I disabled and reinitialized U1 on the laptop hoping that would solve the laptop problem. 

I don't know if any of these 3 things have anything to do with the problem but it was afterwards that I discovered the Ubuntu problem on my desktop computer. Because of the replicating Starting file manager message in the bottom tray, I would assume the problem is with the filesystem and maybe U1. Any suggestions? 

Paul

---

### Post by techunit on 2011-01-15
Hey sorry to hear about your problem. Have you tried the gnome failsafe session? You can choose it before you log-in.

When your computer locks up can you hit Ctrl+Alt+F1 to drop to a terminal?

If you can try this command:

```
top
```

Tell me whats is at the top of the list.

Good Luck

---

### Post by paulholbrook on 2011-01-18
Thank you for looking at my problem.  I have been playing with the system and have a better definition of what is happening.  There are still some things I can still do with it since it doesn't completely lock up.

This problem occurred right after I applied the latest updates via UPDATE MANAGER.  There were no error messages from the update and it said it completed successfully.

 In the first 60 seconds after booting up, everything looks pretty normal.  I can go into PLACES and see my folders and files, however, my U1 synchronised folders do not have a check mark on them any more.  If I go into MY menu, it shows that U1 is active and my data has been synchronised.

Sixty seconds after booting up, STARTING FILE MANAGER begins replicating across the bottom of my screen, all the icons on my desktop disappear, and I can no longer access any of my data via PLACES.  Everything else seems to work OK.  There are a few other problems but I think they are caused by the replicating STARTING FILE MANAGER.  I have also sent this problem description to the Ubuntu One folks but don't have a resolution yet.

I really like Ubuntu and would like to continue using it.

---

### Post by paulholbrook on 2011-01-21
I am giving up trying to solve my Ubuntu problem and think the only solution is to re-install Ubuntu.

PROBLEM: I can't access my data after the first 60 seconds so I can't save my data.  I tried starting a  copy to a flash stick when I first boot up but it gets cancelled after 60 seconds when the replicating STARTING DATA MANAGER messages begins.  Is there a way to save my data?

Paul

---

### Post by gbrainin on 2011-01-21
Boot from a live CD/USB and you should be able to access (and copy) your data before reinstalling.

---

### Post by paulholbrook on 2011-02-05
I re-installed Ubuntu and the problem went away.

---

### Post by b18b on 2011-02-22
You mean the only solution to this problem is to do a re-install?  Attached is a screenshot of the issue I am having.  I think its the same.... 10's maybe hundreds of instances of "Starting Filemanager".

After this problem runs its course the machine runs fine.  I would not mind too much if it wasn't for the fact that this is on a notebook that gets started and stopped several times a day.

---

### Post by itmas on 2011-04-20
Has anyone found a reason or solution to this.

Running 10.04

This error started for me after enabling xinerama on my nvidia card.

I run two screens with compiz running and have been trying to find a way to move programs from one screen to another. I didn't want to go with twinview because I wanted to run programs fullscreen in either of the screens.

After turning on xinerama and rebooting, one screen had gnome gui running, the other had cairo-dock running but no gnome gui and down the bottom of the screen was 30 or more instances of "Starting File Manager". 

Occasionally they go away, but come back for no apparent reason.

I reverted to my backed up xorg.conf file and got the gnome gui running on both screens, but still am getting the "starting file manager" running on the bottom of the screens.

I have looked through the logs files, but cannot find anything to point to. 

Is anyone able to give me a tip on where I should be looking to try to find the root cause of this error?

Thanks.

---

