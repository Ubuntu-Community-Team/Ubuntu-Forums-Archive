---
title: "Processes running at start-up"
date: 2008-05-08
forum: Desktop Environments
---

### Post by LeeU on 2008-05-08
I am running Ubuntu 7.10, which I just loaded last week on a clean new hard drive. I also have a second, smaller hard drive. Once the system is started and the desktop displayed, about 8-10 seconds later, the light on the hard drive begins blinking and "something" loads or runs a process. If I load Firefox or Claws Mail before the "processing" starts, they will freeze and the system has to be re-started. After that the light on the hard drive blinks every two seconds. This is a new hard drive. I am on a network but all of this also happens without any other computer running on the network. The three computers are connected by a router.

Anybody have any idea what is happening here?

---

### Post by LeoSolaris on 2008-05-09
Go to Sessions, it's under System->Preferences->Sessions

The first tab is all of the daemons set to start when you log in. Second one is all of the processes running at the moment. (Although System monitor is a little more precise. You can also use terminal based managers, like htop.) Check one them to see if anything is hogging up your resources.

Have you installed anything other than the fresh install? Did you do the updates? (basics just to rule them out) Have you installed anything other than software from the repos, like IBM's Office? (Lotus Office is slick, but it still has a couple of broken parts, like soffice.bin running in the background constantly.)

There is probably a better way to check those processes, but I would look through them for anything you don't need, and shut it off. (Check around and google them to make sure of what they do before shutting them off, so you don't shut off something important.)

Your second hard drive, is it set to automatically mount at system start?

Another good way to check what's going on would be to set up conky (lot's of howtos on the forums) so it starts at login and have it display what is running.

If this is a little incoherant, my appologies, it's really late for me and I am tired.

---

### Post by llebegue on 2008-05-09
Could that be  indexing process of Tracker ?

In "System -> Preferences -> Search and indexing" is tracker activated ?

---

### Post by LeeU on 2008-05-09
Yes, it seems it was Tracker. I have turned it off and the processes at the beginning have stopped except I still have two things:

1. The hard drive light still blinks every two seconds; and

2. When I first start the computer, after starting Firefox and Claws Mail, it freezes and I have to do a reboot, then it seems to run fine. I'm just hoping the system doesn't crash from the reboots. There must be something here ...

---

