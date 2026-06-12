---
title: "Invalid cd detected"
date: 2009-01-11
forum: General Help
---

### Post by gr4sshoper645 on 2009-01-11
Hi there,

Have been a long windows user, currently with vista, have decided to have a change.  Downloaded the .iso file and copied it to a cd.  When I try run the installation - either at startup or while logged in, i get an error: "invalid cd detected".  Can someone tell me how to resolve this issue and get ubuntu installed on my laptop.  

Thanks heaps!

---

### Post by sendblink23 on 2009-01-11
> **gr4sshoper645 said:**
> Hi there,

Have been a long windows user, currently with vista, have decided to have a change.  Downloaded the .iso file and copied it to a cd.  When I try run the installation - either at startup or while logged in, i get an error: "invalid cd detected".  Can someone tell me how to resolve this issue and get ubuntu installed on my laptop.  

Thanks heaps!

Also what do u mean logged in?  U dont log in when you use  Livecd of Ubuntu..  maybe your talking about something else  not sure im confused...


Probably is a currupted Ubuntu iso you downloaded...  not  sure my suggestion download it again make sure its from ubuntu website your download

well anyways I hope someone else provides help  better than my suggestion


also burn the iso with  infrarecord  its free   search for it on google, use the lowest possinle recording speed  1x  or 2x  for ensure its a perfect  burn of the iso

---

### Post by gr4sshoper645 on 2009-01-11
HI there,

Thanks for your reply.  When i say logged in, I mean logged in to vista.  Sorry for the confusion.  I am currently using imgburn and it still doesn't seem to work on the lowest speed.

---

### Post by DeMus on 2009-01-11
> **gr4sshoper645 said:**
> HI there,

Thanks for your reply.  When i say logged in, I mean logged in to vista.  Sorry for the confusion.  I am currently using imgburn and it still doesn't seem to work on the lowest speed.

Two questions:
1) How do you burn the .ISO file? Is it copied as an .ISO file to your CD or is it unpacked and are the files, originally in the .ISo file, copied to CD?
2) How do you start the installation process? You have to re-boot your computer and let it boot from CD to get to Ubuntu. Then you get a choice of using the live CD, which is totally run from CD so nothing changes on your harddisk, or you chose to install Ubuntu.
Then you have to tell the install program where and how to install it.

DeMus

---

### Post by gr4sshoper645 on 2009-01-11
Hi there,

I did not just copy the iso file to the CD.  I used Imgburn software to burn the iso file to the cd.  Its copied over correctly.

Yes, I did start the installation by rebooting my computer, and i get the same error.

Thanks for your help.

---

### Post by gr4sshoper645 on 2009-01-12
Anyone else?

---

### Post by Snow986 on 2009-01-12
> **gr4sshoper645 said:**
> Anyone else?

  To be a little more clear can you tell us the steps you took to start the installation.  Did you actually boot TO the cd drive?

---

### Post by gr4sshoper645 on 2009-01-12
Yes, I restarted the computer, went to bios and change it to boot from cd first, then it opened up, i selected "try without installing" and i get the error.  I get the error no matter what option I select.

---

### Post by Snow986 on 2009-01-12
Since it does bring up ubuntu then I would think it must be a corrupt version of the iso.  Did you download it here?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by gr4sshoper645 on 2009-01-12
Yes, i downloaded it from there.  I really will only download it from there if I know it will work.  I allready downloaded it from there and since its such a big file it takes so long.

---

### Post by Snow986 on 2009-01-12
Have you tried burning it to a dvd instead of cd?  Or trying a different burning program?  Either might solve your issue.  Or try the disc on another computer.  If you get the error then it is certainly a corrupt iso.

---

### Post by gr4sshoper645 on 2009-01-15
> **Snow986 said:**
> Have you tried burning it to a dvd instead of cd?  Or trying a different burning program?  Either might solve your issue.  Or try the disc on another computer.  If you get the error then it is certainly a corrupt iso.

I tried burning to a dvd, cd-rw and cd-r all with the same results.  I could try downloading again, but only if this will resolve the problem.

---

### Post by mcduck on 2009-01-15
In Windows, what do you see inside the CD if you open it with the file manager?

---

### Post by ajcham on 2009-01-15
Try generating an md5sum of the CD or iso you have, and comparing it to the appropriate example below.  You can get an md5sum program for Windows from [here]("http://md5deep.sourceforge.net/").

**MD5SUMs for Ubuntu ISOs:** [SIZE="1"](from [http://releases.ubuntu.com/releases/intrepid/MD5SUMS](http://releases.ubuntu.com/releases/intrepid/MD5SUMS))[/SIZE]
ea6d44667ea3fd435954d6e1f0e89122 *ubuntu-8.10-alternate-amd64.iso
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso
f9cdb7e9ad85263dde17f8fc81a6305b *ubuntu-8.10-desktop-amd64.iso
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso (this is most probably the one you want)
8d35fea8c16597a6f4dd07f8e18e2166 *ubuntu-8.10-mid-lpia.img
e3028a105a083339be8e5af5afbe7444 *ubuntu-8.10-server-amd64.iso
a2ec9975a91e1228c8292ed9799dc302 *ubuntu-8.10-server-i386.iso
2796c696ab368415a30fddc8278e08b0 *wubi.exe

---

