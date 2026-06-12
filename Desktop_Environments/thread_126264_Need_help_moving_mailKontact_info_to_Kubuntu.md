---
title: "Need help moving mail/Kontact info to Kubuntu"
date: 2006-02-06
forum: Desktop Environments
---

### Post by mattsen on 2006-02-06
Hi ... I'm just barely beginning to find my way around in [K]ubuntu ... so please be gentle :-) (and dumb things down, where possible).

In any case, I'm in the process of moving from Mandriva (cooker), and would like to just carry my mail over from Kontact/Kmail in Mandriva to Kubuntu.  I *thought* it would be as simple as bringing a copy of the .kde and Mail dirs over, but apparently not.  (I think my main problem may be a misunderstanding with respect to users/ownership/permissions, which are apparently handled somewhat differently here than in Mdv.)

In any case, moved the Mail and .kde dirs over, but I cannot get into Kontact/Kmail at all, with "not a valid directory/do not have permission"-type errors at attempt to start up.  I had done a **chown -R [username]:[username] *** to change permissions (substituting my username as appropriate), and it *seemed* to do so, but the permissions errors remain.

Again, I'm an absolute Kubuntu beginner still (and my skills in Mandriva weren't exactly advanced or stellar, though I could get around for the past couple of years with few problems), so any pointers, either to correcting the permissions problem or with respect to how best to move the mail over successfully, would be much appreciated.  TIA.

---

### Post by MartinG on 2006-02-06
Did you try running the chown command with sudo? If the transferred files are not in your user name then ppain chown will have no effect.

If this isn't the answer, I think it may be linked to user IDs (uid).  (K)Ubuntu gives the main user a uid of 1000 (check with "id <username>"), but Mandriva might do something else (1001, 501, ...).  You may need to repeat "sudo chown" but using 1000:1000 in place of username:groupname.

---

### Post by mattsen on 2006-02-06
[QUOTE=MartinG]Did you try running the chown command with sudo? If the transferred files are not in your user name then ppain chown will have no effect.

If this isn't the answer, I think it may be linked to user IDs (uid).  (K)Ubuntu gives the main user a uid of 1000 (check with "id <username>"), but Mandriva might do something else (1001, 501, ...).  You may need to repeat "sudo chown" but using 1000:1000 in place of username:groupname.[/QUOTE]

Been there, done that with sudo, 1000:1000, etc., with no change; still the no permission errors.  If I look at the file and folder properties, they show me as owning, with read/write privileges and all that good stuff, but there's something missing somewhere along the line (other than my understanding of this whole mess, that is).

Admittedly, the whole sudo thing is new to me; no need for it in Mdv, so it's taking some getting used to.

Things have *got to* be easier than I'm making them for myself, somehow.  Color me very frustrated at this point. I really don't want to have to start everything from scratch again, or to have to retain my Mandriva installation forever just to access mail and other files.

??

---

### Post by MartinG on 2006-02-06
[QUOTE=mattsen]Been there, done that with sudo, 1000:1000, etc., with no change; still the no permission errors.  If I look at the file and folder properties, they show me as owning, with read/write privileges and all that good stuff, but there's something missing somewhere along the line (other than my understanding of this whole mess, that is).

Admittedly, the whole sudo thing is new to me; no need for it in Mdv, so it's taking some getting used to.

Things have *got to* be easier than I'm making them for myself, somehow.  Color me very frustrated at this point. I really don't want to have to start everything from scratch again, or to have to retain my Mandriva installation forever just to access mail and other files.

??[/QUOTE]OK, on further thought I think this may be a Kmail problem disguised as permissions (sort of).  When you started this process, had you already used Kontact/Kmail? Or did you copy the Mail directory across and *then* try to start up?  On inspecting my kmailrc file it seems that Kmail uses its own coding to identify folders etc.

If you copied things first, may I suggest that you rename your Mail directory (e.g. MyMail) and then start KMail, and let it make its own folder structure. Then use File->Import Messages->Import Kmail MailDirs & Folder Structure to add your stuff. (If successful you can then delete MyMail, or for safety's sake rename it again to MyMailOld until you're sure it's all worked.)

---

### Post by mattsen on 2006-02-06
[QUOTE=MartinG]...When you started this process, had you already used Kontact/Kmail? Or did you copy the Mail directory across and *then* try to start up?  On inspecting my kmailrc file it seems that Kmail uses its own coding to identify folders etc.[/QUOTE]

Hadn't "used" it, but had fired it up once and then shut 'er back down.

[QUOTE=MartinG]If you copied things first, may I suggest that you rename your Mail directory (e.g. MyMail) and then start KMail, and let it make its own folder structure. Then use File->Import Messages->Import Kmail MailDirs & Folder Structure to add your stuff. (If successful you can then delete MyMail, or for safety's sake rename it again to MyMailOld until you're sure it's all worked.)[/QUOTE]

Starting my work now, so don't get to play again until later in the day.  I'll try renaming the Mail folder(s) out of the way and let it create anew, then try the Import... route.  We'll see how that goes.  Thanks.  (Mail is my MAIN thing ... I can live without anything else, pretty much, as long as I've got my mail and a browser.  :-)

---

### Post by mattsen on 2006-02-06
Well, next problem ... any idea why "Import Messages" is grayed-out and inaccessible?

---

### Post by MartinG on 2006-02-06
[QUOTE=mattsen]Well, next problem ... any idea why "Import Messages" is grayed-out and inaccessible?[/QUOTE]Sorry about the delay -- been shopping :(

This took a bit of digging, but what you need is to install the package kmailcvt.  I have the whole of kde-pim installed, which covers a lot more than just Kontact. This automatically installs kmailcvt, but you can install it on its own. Then close and re-start Kontact, and the menu option should be there.

Perhaps I should have twigged?  But IMHO it's a bit obscure to leave such a crucial feature in an optional package.  Maybe now you can get it done!

---

### Post by mattsen on 2006-02-06
[QUOTE=MartinG]Sorry about the delay -- been shopping :([/QUOTE]
No problem -- been sleeping. :)

[QUOTE=MartinG]This took a bit of digging, but what you need is to install the package kmailcvt.  I have the whole of kde-pim installed, which covers a lot more than just Kontact. This automatically installs kmailcvt, but you can install it on its own. Then close and re-start Kontact, and the menu option should be there.[/QUOTE]
That did it ... thanks.  Took forever to import, mark as read, tweak, etc. (and the tweaking continues), but e-mail is operational and usable in Kubuntu now, so many thanks.

*(I still think the whole process should be a whole lot simpler, but... I'm happy to be up and running, anyway.)*

---

