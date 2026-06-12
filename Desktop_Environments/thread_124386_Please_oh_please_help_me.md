---
title: "Please oh please help me"
date: 2006-02-01
forum: Desktop Environments
---

### Post by jcjcmcsc on 2006-02-01
I am a week old in linux world. My problem is that in ubuntu, i cant get the ndiswrapper to install. it keeps asking me for the root acount, and i am lost. pretty silly huh. i have a d-link 520 and if i cant get it to work my wife wants to go back to W#^&*s  [-(  i shutter to think. 
 Linux Rocks \\:D/ 
please please i am so new baby steps :O)

thanks

---

### Post by jasmuz on 2006-02-01
Use "sudo" as a root replacement, and follow this.
Read it here: [https://wiki.ubuntu.com/SetupNdiswrapperHowto]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")

Just jump down to the installing windows drivers bit.

---

### Post by pandionknight on 2006-02-01
I'm a newbie myself and as such do not know what ndiswrapper is, but do know that when you installed Ubuntu, it asked you to supply a Passsword for the Root Account. This is what it asks for when installing new packages/applications. You will need to try and remember what details you entered upon installation.

---

### Post by jcjcmcsc on 2006-02-01
Thanks all,

 I will let you know if it works :O) this is all so greek and i have no programming or linux expirence. but by the crown of neptune i will get this if it takes me 5 sleepless nights  :O) and wow thanks too for such speedy responce.i know i have made the right choice switching to Linux :O)

---

### Post by ipp3l1 on 2006-02-01
[QUOTE=pandionknight] when you installed Ubuntu, it asked you to supply a Passsword for the Root Account. This is what it asks for when installing new packages/applications. You will need to try and remember what details you entered upon installation.[/QUOTE]

Well, ubuntu never actually asks root password(unless you define it by yourself later), and root account is basically disabled in ubuntu, or at least it's never needed. Sudo -command replaces the need of root account in Ubuntu,though it is possible to login as root in terminal (basically it's never needed).

---

### Post by Lord Illidan on 2006-02-01
[quote=pandionknight]I'm a newbie myself and as such do not know what ndiswrapper is, but do know that when you installed Ubuntu, it asked you to supply a Passsword for the Root Account. This is what it asks for when installing new packages/applications. You will need to try and remember what details you entered upon installation.[/quote]

Wrong. Ubuntu does not ask for your root password but for your own user password. The root password is scrambled by default, so you can't use root. You can enable root login, of course, but sudo is generally recommended. It is too easy to break a system or even your profile with root.

Example, running ```
rm * .mp3
``` as root in the /etc directory. You might think that it will delete all mp3s. Wrong. It will actually delete everything. Note the space between the wildcard ( * ) and the .mp3. Need I say, don't try this at home.
Now, with sudo, this will ask you for your password, thus letting you review what you have already written, letting you cancel the process immediately.

---

