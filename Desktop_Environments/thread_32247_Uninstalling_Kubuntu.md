---
title: "Uninstalling Kubuntu"
date: 2005-05-06
forum: Desktop Environments
---

### Post by davih on 2005-05-06
i feel really guilty posting this but.....

(gulp)how i do i uninstall Kubuntu?


...sorry

---

### Post by cdhotfire on 2005-05-06
did you install kubuntu from ubuntu, by apt-get?

---

### Post by davih on 2005-05-06
i installed ubuntu from the intel x86 install cd.

i first dowloaded the file from this site: [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)
and then i burned the file to a cd to use on a different computer

---

### Post by SteveyDevey on 2005-05-06
[QUOTE=davih]i installed ubuntu from the intel x86 install cd.

i first dowloaded the file from this site: [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)
and then i burned the file to a cd to use on a different computer[/QUOTE]
Do you just not want to use it anymore? If not, just format the partition(s) and install something else. (unless I'm misunderstanding you)

---

### Post by davih on 2005-05-06
HOw do i format the partitions?

---

### Post by SteveyDevey on 2005-05-06
[QUOTE=davih]HOw do i format the partitions?[/QUOTE]
 If you're planning on installing an operating system on the drive again, the installer for the operating system will help you do it. It will give you the opportunity to set up the drives and partitions before putting any files on the drive.

If you are just going to use the drive for storage on another computer, it would be easier to tell you how to do it from that computer, once it's in there.

---

### Post by davih on 2005-05-06
See i put in the windows 98 install cd. and it said that it couldnt find a "c drive" to write to.  I think it has something to do with windows not being compatible with Linux native and linux swap partitions.
I think have to use the fdisk tool to delete the partitions, but i dont know how to use it, if i have to use it at all

---

### Post by johnprgr on 2005-05-06
I haven't installed win98 in alot of years, but I believe that the dos fdisk program will delete the partitions.  If I remember correctly it is fairly self-explanitory once you run the program  

I know that "fdisk /mbr" will get rid of grub or lilo for you.

Another way may be to boot with the ubuntu install cd and at the point where you select and format partions just delete them all and make win32 partitions instead.  Once they are formated win32 just reboot the computer using your win98 cd.

Good luck, maybe check out ubuntu again sometime in the future.  Maybe then it will be what your looking for.

Hope this helps

---

### Post by gunnyman on 2005-05-06
You are going to need Fdisk.
fdisk then choose to delete the non dos partition.
Then create a partition make it primary 
after that reboot
after that, do fdisk /mbr
that will make your C  drive bootable thus enabling the install of Win 98.

---

### Post by davih on 2005-05-07
"at the point where you select and format partions just delete them all and make win32 partitions instead"

How do i go about doing this?

---

### Post by ludi on 2005-05-07
[QUOTE=davih]"at the point where you select and format partions just delete them all and make win32 partitions instead"

How do i go about doing this?[/QUOTE]
Please, don't missunderstand but this situation is really ridiculous... Why don't you try to read some how-to, faqs, books, magazines etc to learn the basic (really basic) of computers?
The first thing that you have to know is how the "stuff works", and the computer is the stuff in this case. Something like drive a car and don't understand what the engine do.
If you don't want to learn it, just pay some guy to do the job...

---

