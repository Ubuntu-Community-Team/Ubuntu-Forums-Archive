---
title: "Creating Persistent USB Ubuntu does not work in Ibex"
date: 2008-12-04
forum: General Help
---

### Post by slyron on 2008-12-04
Hi, I've got a 8gb PNY Attache' USB and I've been trying really hard for the few days to get a persistent Ubuntu setup on the drive for work/school. I've tried USB Creator as installed in Ibex, and I've tried this:
[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

...with no luck. It will boot fine...until I make any changes, and then I get messages like: "Push F1 to retry boot" and the like as the machine boots up. 

I've tried a range of changes in the Ubuntu environment to see if little or large changes persist: I can't make a simple text file on the desktop, can't change the background, can't remove an icon, can't change compiz settings. 

Am I doing something wrong here?

---

### Post by collinp on 2008-12-04
This may assist you (Ignore the Alpha 6 stuff, this was made before Intrepid was a "full" release):[http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22](http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22)

---

### Post by cmay on 2008-12-04
did you get the usb creator in ubuntu working and if so how. i ask since i have been trying to get a good feeling of the program and so far i done a few succes full start up live cd installs for install on asus eee pc but as far as persistent i am also a bit currius how its done. you can however very easy use both puppy linux and damn small linux for having perstient installs which allows you to save your changes. i run a puppy on a usb stick which i am going to remaster into a cd again using the tols for it in puppy.

---

### Post by slyron on 2008-12-04
"Hellow", thanks for the link, but I've tried it and Unetbootin doesn't allow for persistence (can't save changes). cmay, I just found USB Creator in the System menu in Gnome. It's built into Ibex.

---

### Post by slyron on 2008-12-05
I'm reading in some places that an 8gb USB might not work so well with persistent booting....

---

### Post by cmay on 2008-12-05
> **slyron said:**
> "Hellow", thanks for the link, but I've tried it and Unetbootin doesn't allow for persistence (can't save changes). cmay, I just found USB Creator in the System menu in Gnome. It's built into Ibex.
yes it is. i have been playing with it for some time. it seems to work ok with all debian based cd sets but it has to be formatted as fat32 to work and it works better if you use it as following. download the iso image and have the usb stick formatted in fat32 and no partions on it. wiht the flags set to boot and then just ask the usb creator to create a usb stick from the iso image and it ask to format the stick which just clik ok then it works. i have the eeebuntu  live cd on a usb stick for my asus eee pc but its not perstent. there is a option to make it perstistent but i do not know how it is done yet.  but as i said if the goal is to have a system you can carrie then a usb stick of poppy or damn small linux is way more easy i think. i actually use both as i like to swich from distro to distro sometimes but i do not want to erase a partion of a working and ok functioníng ubuntu so i try usb stick distros instead for a while. 
i will follow this tread so if you find anything out then please let me know. 
thanks for the reply and good luck with the project. :)

---

### Post by slyron on 2008-12-05
Ok, thank you for the information cmay. I'll keep trying. Obviously this is something that Jaunty Jackel will have to improve on.

---

