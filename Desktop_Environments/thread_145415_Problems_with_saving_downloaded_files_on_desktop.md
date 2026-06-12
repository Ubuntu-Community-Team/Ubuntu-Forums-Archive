---
title: "Problems with saving downloaded files on desktop"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Naresh_4 on 2006-03-16
Hi there, im a new user to ubuntu, and ive been having this problem for quite a while now. what happens is that when i downlad a file via mozilla browser, then save the file on my desktop, i cant see the file on my desktop. i cannot also access the file via terminal commands, and the terminal just says that the file does not exist.  however, when i click on the link in the mozilla download manager, that says where my files are located, it opens up the directory of my desktop and i can see my files. however, the directory ONLY contains files that i have downloaded and no others. i cannot copy the files from this mozilla Desktop directory  onto my actual desktop. in the meantime, my terminal is going crazy with these messages:

(file-roller:1787): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
FRArchive::action_started: 0
*** loading the extensions datasource

(nautilus:1862): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:1886): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (nautilus:1735): WARNING **: Possibly invalid new URI ''
This can cause subtle evils like #48423

** (nautilus:1735): WARNING **: Possibly invalid new URI ''
This can cause subtle evils like #48423

** (nautilus:1735): WARNING **: Possibly invalid new URI ''
This can cause subtle evils like #48423

(nautilus:2027): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:2154): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:2214): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

i would think this would be some problem with permissions or something, im not sure, any help would be appreciated :)

thanks

---

### Post by kaamos on 2006-03-16
Err.. Are you running mozilla as root? :shock:

---

### Post by Naresh_4 on 2006-03-16
well im not sure exactly, when i open up a terminal, and launch mozilla as root user, or whether im a standard user, the same thing happens. i just tried it again, i downloaded a file, viewed it via the link in the mozilla file download manager, and this message comes up: 

(nautilus:3049): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

i just noticed however that its happening with other apps aswell, for example gedit:

(gedit:2838): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:2849): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:2857): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:2878): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

i have no idea wats going on.

---

### Post by kaamos on 2006-03-16
(Don't even try running as root, it a disaster waiting to happen if you do)

What is the whole path (/blaa/blaa/folder) of the folder that the download manager opens?

---

### Post by Naresh_4 on 2006-03-16
i dont know what just happened, but now the download manager cant open the file at all, its saying "file.pdf doesn not exist. it may have been renamed, moved or deleted since it was downloaded" however mozilla says that the file should be on my desktop. but it isnt.

---

### Post by engla on 2006-03-16
If you have been running as root, look at root's desktop.
Poke around in the /root directory

---

### Post by Naresh_4 on 2006-03-17
thanks for the help, i finally figured out what was going on. i was running mozilla as root! i advise pple not to do this in the future, it screwed everything up. thanks again :)

---

