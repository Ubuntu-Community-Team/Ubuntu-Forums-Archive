---
title: "Firefox crashes on startup"
date: 2009-05-28
forum: General Help
---

### Post by sachins on 2009-05-28
Hello all,

I have a wierd problem. I was happily using firefox till last week and suddenly firefox refueses to start. On the console after typing 'firefox' it just exits. Doing a 'firefox &' shows me that it has exited with error code 1.

I have tried running firefox in safe mode and removed the ~/.mozilla/firefox directory. I have re-installed firefox multiple times to no avail.

I am running Ubuntu Intrepid and firefox version is 3.0.10. My guess was that after upgrading from 3.0.3 to 3.0.10 the problem started happening. I downgraded FF to 3.0.3 but still the problem persists.

Thinking that the problem would be with the Nvidia Cuda driver I installed in between, I removed it and am back to the generic video driver but again, it made no difference.

I am going mad here, there is no error message for me to work upon, please suggest something.

Sachin.

---

### Post by upbeat.linux on 2009-05-28
I realize that you removed the .mozilla directory but have you tried recreating your user profile and launching firefox?  Try this from the command line:

```
firefox -profilemanager
```

Create a new profile and launch firefox with it. Does the issue persist?

If you are unable to access the profile manager you can alternatively try:

```
firefox -no-remote -P
```

or

```
firefox -a asdf
```

---

### Post by sachins on 2009-05-29
I have already tried all that. The issue persists though :(

The interesting thing is that when I open firefox using the profilemanager switch, the selection dialog box opens and I can select, rename, delete or create a new profile. But after that again firefox crashes with the same error code.

Sachin.

---

### Post by Soul-Sing on 2009-05-29
Make a backup copy of your .mozilla folder then PURGE Firefox, rather than just uninstall/reinstall, then reinstall and see what you have..

---

### Post by sachins on 2009-05-30
Done that too. I am assuming that by 'purge' you mean the 'completely remove' option in Synaptic.

I think it's a problem greater than just missing dependencies. I have downloaded a fresh copy of firefox from the official website and ran it in it's own folder but its giving me the same error.

Sachin.

---

### Post by Bert_421 on 2009-06-22
sachins

did you find the answer to your problem?
 i am starting to have this issue Firefox, starting but no page is displayed (blank) No Blank is not my startup page.

Also does Ubuntu have a menu to force close program that will close programs that are not responding? ( taskmanager ) I have closed Firefox and try to open it later but system tell me that it is still open. i am having to log off and back on to clear the error

---

### Post by sachins on 2009-06-23
No I didn't get any answer to my query. I switched to Opera on my Ubuntu but I'm not that happy about it.

If you want to close firefox then go to the terminal, type 'ps ax | grep firefox'. This will show you the process id of firefox then you can issue the command 'kill <process id>' to kill that process.

Sachin.

---

### Post by Bert_421 on 2009-06-23
Man hate to here that!!  i tried opera not a big fan of it. i guess i will stay with IE8 
thanks for the kill command.

---

### Post by blueridgedog on 2009-06-23
One item to try is to remove the .mozilla directory in your home directory (backup or export any bookmarks).  You can see it with ls -al or with show hidden files in nautilus.  Doing this will cause you to loose all your firefox settings, bookmarks and plugins.

---

### Post by sachins on 2009-06-24
blueridgedog: I've already tried that to no avail. The problem seems to be something else altogether.

---

### Post by acope on 2009-11-09
Hi,
Having the same problem with firefox not starting.
I've recently upgraded from Kubuntu 9.04 to 9.10, and now when I run firefox, it silently exits with error code 1.
I've tried removing, purging and reinstalling, but to no avail.

$ firefox -v
Mozilla Firefox 3.5.6pre, Copyright (c) 1998 - 2009 mozilla.org
$ firefox
$ echo $?
1

I've tried renaming my .mozilla folder first, but same result.

The only thing that's a clue is that when I first log in and start firefox, it complains that it has no permissions in ~/.gnome2_private/ which is weird, because if I do:
$ ls -ld .gnome2_private
drwx------ 2 andrew andrew 6 2006-08-31 10:58 .gnome2_private

and then run firefox again, it then complains that it has no permissions in ~/.gnome2/accels/ which it does have:
$ ls -ld .gnome2/accels
drwx------ 2 andrew andrew 6 2006-08-31 10:58 .gnome2/accels

and then if I run firefox again after doing the above, it stops complaining and just silently exits to the command line.

Anyone got any ideas?

---

### Post by waj1122 on 2009-11-09
You probably borked up the ownership of your profile. To fix it, just run the following command in a terminal:

sudo chown -R youruser:youruser ~/.mozilla

(youruser == your actual username on the computer)

Can you run gksudo firefox from terminal? (Never use sudo firefox).

---

### Post by Ajay Ramaseshan on 2010-02-09
Hello ppl . I have a similar problem on Firefox crashing.
I was trying to resize my Linux partitions but got an error. So I repeated the task using the Live Cd.

But when I loggeed on to my system I found that Firefox crashes on startup. I checked up my Home Folder and found out that some files are missing. I gave ls .mozilla and it gave me this error:
ls: cannot access .mozilla: Input/output error
I am getting the same error with some more files ie
.profile,.bash_logout:examples.desktop and Documents same Input/Output error. Is there any way to recover these files? Or have they been deleted permanently? and what will solve my Firefox problem?

---

