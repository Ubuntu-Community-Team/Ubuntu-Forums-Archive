---
title: "Firefox Bookmarks Problem"
date: 2012-04-15
forum: Desktop Environments
---

### Post by Geffers on 2012-04-15
Got a message that Firefox's files are in use by another application.

Followed the advice on the help file to resolve it and the eroor message has gone but I cannot restore any of the backed up .json files, just get the message 'Unable to process the backup file' whichever back up I choose.

There is data within all the files.

Geffers

---

### Post by lovinglinux on 2012-04-15
What advice exactly did you follow?

---

### Post by Geffers on 2012-04-16
> **lovinglinux said:**
> What advice exactly did you follow?

Deleted places.sqlite then restarted.

This cured the error on startup, I then tried to restore bookmarks, there are 11 files in the Bookmarks Backup folder but if I try to restore any of them I get this error;

Unable to process the backup file'

Geffers

---

### Post by lovinglinux on 2012-04-16
> **Geffers said:**
> Deleted places.sqlite then restarted.

This cured the error on startup, I then tried to restore bookmarks, there are 11 files in the Bookmarks Backup folder but if I try to restore any of them I get this error;

Unable to process the backup file'

Geffers

Do you still have the *places.sqlite* file in your trash?

---

### Post by Geffers on 2012-04-17
> **lovinglinux said:**
> Do you still have the *places.sqlite* file in your trash?

Oh yes, I restored it so I am back to seeing the message 'The bookmark and history system will not be functional because one of Firefox's files are in use by another application.

Geffers

---

### Post by lovinglinux on 2012-04-19
> **Geffers said:**
> Oh yes, I restored it so I am back to seeing the message 'The bookmark and history system will not be functional because one of Firefox's files are in use by another application.

Geffers

Good. Now try to start Firefox with this command:

```
firefox -safe-mode -no-remote
```

If it starts, open the bookmark manager, export your bookmarks as HTML, close Firefox, delete *places.sqlite*, open Firefox in normal mode, import the HTML backup.

Le me know if it works. If not, upload the *places.sqlite* to somewhere private, send me the download link trough PM and will try to fix it.

---

### Post by Geffers on 2012-04-19
> **lovinglinux said:**
> Good. Now try to start Firefox with this command:

```
firefox -safe-mode -no-remote
```

If it starts, open the bookmark manager, export your bookmarks as HTML, close Firefox, delete *places.sqlite*, open Firefox in normal mode, import the HTML backup.

Le me know if it works. If not, upload the *places.sqlite* to somewhere private, send me the download link trough PM and will try to fix it.

I've got nothing in my bookmarks, since I got the original message of a file used by Firefox in use by another application I haven't got any bookmarks. I do have eleven files in the backup folder but unable to import them/

Geffers

---

### Post by lovinglinux on 2012-04-19
> **Geffers said:**
> I've got nothing in my bookmarks, since I got the original message of a file used by Firefox in use by another application I haven't got any bookmarks. I do have eleven files in the backup folder but unable to import them/

Geffers

Open Firefox profile folder, located under ~/.mozilla/firefox/xxxx.default/ and delete the file **lock**. Try to start Firefox again.

---

### Post by Geffers on 2012-04-20
> **lovinglinux said:**
> Open Firefox profile folder, located under ~/.mozilla/firefox/xxxx.default/ and delete the file **lock**. Try to start Firefox again.

Did that then followed your previous instruction, again no bookmarks shown and same error message if I try to restore the stored bookmarks.

Geffers

---

### Post by lovinglinux on 2012-04-21
> **Geffers said:**
> Did that then followed your previous instruction, again no bookmarks shown and same error message if I try to restore the stored bookmarks.

Geffers

Upload the *places.sqlite* and some json backups to somewhere private and send me the link by private message. I will try to fix it and send you back a working file.

---

### Post by XDan on 2012-04-21
I had a similar problem.

It was caused by a Firefox addon called DownloadHelper.

I fixed it by reapplying permissions setting my user as owner on the the .mozilla folder in my home directory.

---

### Post by Geffers on 2012-04-22
> **lovinglinux said:**
> Upload the *places.sqlite* and some json backups to somewhere private and send me the link by private message. I will try to fix it and send you back a working file.

Thank you very much for all your help.

I have sent a private message with a download link.

Fortunately all my passwords and usernames are still working.

I wonder why Mozilla went away from bookmarks as html files, everything can read those but scripts just add complications.

Geffers

---

### Post by lovinglinux on 2012-04-22
The files you sent me were not corrupt.

You might want to try to re-install firefox and also try a clean user profile.

```
sudo apt-get install --reinstall firefox
```

```
firefox -P
```

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Geffers on 2012-04-26
> **lovinglinux said:**
> The files you sent me were not corrupt.

You might want to try to re-install firefox and also try a clean user profile.

```
sudo apt-get install --reinstall firefox
```

```
firefox -P
```

Please attach the firefox-report.txt file generated in your desktop after running the commands below:



After reinstall then entering firefox -P I got the same error message saying 'The Bookmark and History system will not function because one of Firefox's files are in use by another application - Some security software can cause this problem'.

I cut and pasted your suggested file generation commands and attach the file.

Geffers

---

### Post by lovinglinux on 2012-04-26
Check if you are the owner of the ~/.mozilla folder and check if AppArmor is allowing Firefox to save there.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

[http://support.mozilla.org/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional](http://support.mozilla.org/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional)

[http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox](http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox)

---

### Post by Geffers on 2012-04-28
> **XDan said:**
> I had a similar problem.

It was caused by a Firefox addon called DownloadHelper.

I fixed it by reapplying permissions setting my user as owner on the the .mozilla folder in my home directory.

I do have download helper but my permissions on the folder seem OK.

How did you narrow it down to downloadHelper

Geffers

---

### Post by Geffers on 2012-04-28
> **lovinglinux said:**
> Check if you are the owner of the ~/.mozilla folder and check if AppArmor is allowing Firefox to save there.

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

[http://support.mozilla.org/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional](http://support.mozilla.org/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional)

[http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox](http://kb.mozillazine.org/Bookmarks_history_and_toolbar_buttons_not_working_-_Firefox)

Strangely, I've never used Firefox profiles before but started it with the profile manager, created another user instead of the solitary default.

Backup bookmarks now restore fine and work OK but saved passwords not valid although they worked fine in the dodgy profile.

Not sure this is a remedy or a fix but thanks very much for your help.

Geffers

---

### Post by lovinglinux on 2012-04-28
> **Geffers said:**
> Strangely, I've never used Firefox profiles before but started it with the profile manager, created another user instead of the solitary default.

Backup bookmarks now restore fine and work OK but saved passwords not valid although they worked fine in the dodgy profile.

Not sure this is a remedy or a fix but thanks very much for your help.

Geffers

Copy signons.sqlite and key3.db to the new profile.

---

### Post by Geffers on 2012-04-29
> **lovinglinux said:**
> Copy signons.sqlite and key3.db to the new profile.

Thank you, initially Firefox again threw a wobbly and gave me an error message but I copied the files using Nautilus as root so the transferred files ended up with root ownership.

Changed permissions and all now seems to be OK.

I wonder what caused the problem in the first place but thank you very much for all your help.

Geffers

---

### Post by lovinglinux on 2012-04-29
> **Geffers said:**
> Thank you, initially Firefox again threw a wobbly and gave me an error message but I copied the files using Nautilus as root so the transferred files ended up with root ownership.

Changed permissions and all now seems to be OK.

I wonder what caused the problem in the first place but thank you very much for all your help.

Geffers

Yes, most likely that the ownership caused the problem in the first place. Make sure all folders and files under ~/.mozilla are owned by you and never use SUDO to start Firefox or to copy files from the profile.

---

