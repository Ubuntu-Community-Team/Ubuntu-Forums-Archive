---
title: "ubuntu 7.10 locks up reguardly while playing wow?"
date: 2008-04-17
forum: Desktop Environments
---

### Post by Intangir on 2008-04-17
i play wow, i played it on 6.10? forever, without any issues

i recently installed 7.10 of ubuntu, and its running very well MOST of the time

but every so often, like usually once every day or once every few hours it locks up on me for 10 to 30 seconds.. i turned off alot of settings to see if it helped, it hasnt, its locking up on me for 10-30 seconds every hour or even every 30 minutes now.. its happening so damn often its making the game totally unplayable

i tried to figure out if it was cause of other programs running, i cant find tell that any other apps are running that could be causing it ,, i have no idea whats causing it.. maybe nvidia drivers?

its not an overheating issue if thats what your thinking, i checked my cpu is very cool

also it worked for 2 years on 6.10 without any issue

---

### Post by Intangir on 2008-04-17
i think the culprit is gtk-window-decorator

---

### Post by daengbo on 2008-04-17
Yeah. Definitely turn off desktop effects before you play any 3D game, especially under Wine.

---

### Post by Intangir on 2008-04-17
ah, well i tried running wow with it on, and it mostly ran fine

and even when i started to wonder if that was the problem, i ran metacity --replace to remove the compiz

but apparently it left gtk-window-decorator running, which i think is the problem

i may just try another window decorator and see if it doesnt happen at all even with compiz running

just flat metacity does behave a little better with viewport and alt tabbing though

---

### Post by Intangir on 2008-04-17
its not gtk-window-decorator..

im not sure what it is.. but its still doing it..
with all desktop effects turned off

---

### Post by Intangir on 2008-04-17
im gonna have to downgrade back to 6.10 or whatever i had before if i cant figure this out...

this is unusable for games as it is..  30 second locks ups 2-3 times an hour ruins any seriously competitive gaming

---

### Post by Intangir on 2008-04-17
i tried disabled avahi and nm-applet
and tried setting all my network stuff to manually configured

i cant tell if its worked yet.. avahi-autoid or something like that keeps somehow magically restarting, i dont know how, or what is starting it

i got one lockup after disabling everything but noticed avahi-autoid was running again.. so maybe it is causing it

i noticed a bunch of avahi and dhcp stuff in my syslog too
it goes on all day long, it checked for dhcp responces on interfaces that arent even being used

i disabled them but it still checks...

---

### Post by daengbo on 2008-04-17
> **Intangir said:**
> i tried disabled avahi and nm-applet
and tried setting all my network stuff to manually configured

i cant tell if its worked yet.. avahi-autoid or something like that keeps somehow magically restarting, i dont know how, or what is starting it

i got one lockup after disabling everything but noticed avahi-autoid was running again.. so maybe it is causing it

i noticed a bunch of avahi and dhcp stuff in my syslog too
it goes on all day long, it checked for dhcp responces on interfaces that arent even being used

i disabled them but it still checks...

Calm down and take a deep breath.

The first thing to do is to turn off effects before you play. Compiz is new and doesn't play well with a lot of 3D games and especially Wine. Turn it off through System > Preferences > Appearances, not using --replace.

Secondly, how is your network configured? You're doing a lot of random stuff here, hoping that it'll solve your problem. It's possible that your IP is expiring every hour and DHCP is requesting a new one. If that's the case, you can set up a static IP or change your router to give longer lease times for DHCP.

Thirdly, you need to remain clam. I understand that WoW is important and that you need it to work. If you are changing too many things, though, no one will know exactly what's causing the problem or when it was fixed. Be systematic about this, eliminating one factor at a time.

---

### Post by Intangir on 2008-04-17
i am calm, i posted all these posts over the corse of like 2 days see

ya i think its network now, but the thing is my router is unchanged since 6.10 which it worked fine with

---

### Post by Intangir on 2008-04-17
do these types of things seem odd?
it keeps re-enabling eth1, even though its not plugged in and not used
kept doing dhcp on it before too

also see how it keeps saying
WARNING: Not loading blacklisted module ipv6

i disabled ipv6 cause it seemed to cause delays on certain connections
but why does it say that so often in the log? i check back and its said that over a dozen times since i booted. i thought it only disabled it at boot and left it disabled


seems quite a few things are going off and going on on their own since 6.10,

```
Apr 17 18:46:21 kefka dhclient: wifi0: unknown hardware address type 801
Apr 17 18:46:21 kefka dhclient: wifi0: unknown hardware address type 801
Apr 17 18:46:21 kefka dhclient: Listening on LPF/eth1/00:0f:ea:8a:d6:c1
Apr 17 18:46:21 kefka dhclient: Sending on   LPF/eth1/00:0f:ea:8a:d6:c1
Apr 17 18:46:21 kefka dhclient: Sending on   Socket/fallback
Apr 17 18:46:21 kefka kernel: [ 4337.407012] sky2 eth1: disabling interface
Apr 17 18:46:21 kefka NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
Apr 17 18:46:21 kefka NetworkManager: <info>  Recreating the device list. 
Apr 17 18:46:21 kefka kernel: [ 4337.440460] sky2 eth1: enabling interface
Apr 17 18:46:21 kefka NetworkManager: <info>  Device list recreated successfully. 
Apr 17 18:46:21 kefka NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
Apr 17 18:46:21 kefka NetworkManager: <info>  Recreating the device list. 
Apr 17 18:46:21 kefka NetworkManager: <info>  Device list recreated successfully. 
Apr 17 18:46:23 kefka NetworkManager: <info>  Going to sleep. 
Apr 17 18:46:23 kefka NetworkManager: <info>  Waking up from sleep. 
Apr 17 18:46:30 kefka modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 17 19:15:23 kefka -- MARK --
Apr 17 19:35:23 kefka -- MARK --
Apr 17 19:55:23 kefka -- MARK --
Apr 17 20:12:39 kefka modprobe: WARNING: Not loading blacklisted module ipv6 
```

---

