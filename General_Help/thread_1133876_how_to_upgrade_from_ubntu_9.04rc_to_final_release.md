---
title: "how to upgrade from ubntu 9.04rc to final release"
date: 2009-04-23
forum: General Help
---

### Post by banana jama on 2009-04-23
im trying to upgrade from the rc to the final version of ubuntu 9.04. when i go to upgrade manager and do a partial upgrade it says two are going to be removed and one added (java 2 text to speech something like that). when i click start it seems to crash(because it just disappear). i've also used sudo apt get update and sudo apt get upgrade. though im allowed to download stuff using these commands i think im still using the rc because when i go to update manager it still says im only allowed to do a partial upgrade. can anyone help?

---

### Post by juancarlospaco on 2009-04-23
Reload, and install all updates, you are done.

---

### Post by Laibcoms on 2009-04-23
I haven't encountered the "you can only do a partial upgrade" yet.  As far as I know, just go to synaptic, click the Reload button, click the Marked All Upgrades button, Apply, you're done.  (Restart if needed)

My Jaunty switched from Beta to RC to Final.

---

### Post by thiagom on 2009-04-23
I´ve got alternate-cd ISO (at work) and copied to my flash drive...
At home i´m using RC, can i upgrade it from iso like this ? 

> sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
then
gksu "sh /cdrom/cdromupgrade"
(from [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading))

---

### Post by gedas0220 on 2009-04-23
how to check what version do i have? rc or final?

---

### Post by thiagom on 2009-04-23
> **gedas0220 said:**
> how to check what version do i have? rc or final?

To find your Ubuntu version: 
lsb_release -a

---

### Post by andy71600 on 2009-04-23
> **thiagom said:**
> To find your Ubuntu version: 
lsb_release -a
Would this mean that I have the final?

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

I tried to update today, but no updates have showed up...

---

### Post by banana jama on 2009-04-23
thanks for the posts i was able to upgrade to 9.04 final ny going to terminal and typing  " sudo apt get dist upgrade" without the "".

---

### Post by thiagom on 2009-04-23
> **andy71600 said:**
> Would this mean that I have the final?

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

I tried to update today, but no updates have showed up...


Yes my friend...Check using "update-manager -d" and "sudo apt-get update", "sudo apt-get dist-upgrade" (without quotes)..
Regards

---

