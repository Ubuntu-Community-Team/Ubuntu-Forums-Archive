---
title: "help can't boot into kde"
date: 2005-07-14
forum: Desktop Environments
---

### Post by arjay1 on 2005-07-14
I have been modifying my org.conf files to try and get dual monitors (that's another story).  A couple of times I was sent to the command prompt because of errors in the config file.  However, I was able to get one screen back by sudo and then vi the org.conf file.  I then typed startx, got to the logon prompts and logged in as usual with my user name.

Insted of getting the kde desktop I got this message

"While trying to start KDE ... no authority to write to /home/rjoss/.ICEauthority.

Could not start ksmserver - check your installation".  Then everything went blank and I had to reboot

After rebooting an icon appeared offering KDE or failsafe.  I chose failsafe and was able to get back into the desktop as root but cannot log in as a user.  

I have not modified any other files

Any help would be much appreciated.

TIA

---

### Post by caspar_wrede on 2005-07-14
[QUOTE=arjay1]I have been modifying my org.conf files to try and get dual monitors (that's another story).  A couple of times I was sent to the command prompt because of errors in the config file.  However, I was able to get one screen back by sudo and then vi the org.conf file.  I then typed startx, got to the logon prompts and logged in as usual with my user name.

Insted of getting the kde desktop I got this message

"While trying to start KDE ... no authority to write to /home/rjoss/.ICEauthority.

Could not start ksmserver - check your installation".  Then everything went blank and I had to reboot

After rebooting an icon appeared offering KDE or failsafe.  I chose failsafe and was able to get back into the desktop as root but cannot log in as a user.  

I have not modified any other files

Any help would be much appreciated.

TIA[/QUOTE]
 How about just getting the original Xorg.conf file and copying it back into place. You can rename your experimental Xorg file and switch back and forth by renaming them.

You can restart the Xserver by pressing ctrl+alt+backspace meaning you don't have to restart the computer each time you make a change.

You can also get to a text console that doesn't require an Xserver by pressing ctrl+alt+F1 to ctrl+alt+F6. Position 7 (i.e. ctr+alt+F7) is where the Xserver lives.

---

### Post by arjay1 on 2005-07-14
Thanks for your quick and helpful reply.  The commands you suggested were new to me and proved very helpful in navigating back and forth.

I saved my experimental xorg.conf file and copied over the original which I had backed up first.  I checked this with a text editor and it was definitely the original.

However, when I rebooted I got the same error messages as in my previous post.  I also saw this as KDE tried to boot up:  "/tmp/k-socket-rjossgxrilc owned by uid 1000 insted of uid 0".  There followed messages about timeouts for .ICEauthority etc.

Does this not mean that my password files or permissions somewhere have been corrupted?

Richard

---

### Post by elsewhere on 2005-07-14
Take a look at [this thread...](http://ubuntuforums.org/showthread.php?t=46614)

*sudo chown rjoss:rjoss /home/rjoss/.ICEauthority* should fix the ownership issue with your .ICEauthority file (I'm assuming based on your error messages that rjoss is your Ubuntu user name, if not just subsitute your correct username).

Hope this helps...

Cheers,
KV

---

### Post by IchBin on 2005-07-14
[QUOTE=elsewhere]Take a look at [this thread...](http://ubuntuforums.org/showthread.php?t=46614)

*sudo chown rjoss:rjoss /home/rjoss/.ICEauthority* should fix the ownership issue with your .ICEauthority file (I'm assuming based on your error messages that rjoss is your Ubuntu user name, if not just subsitute your correct username).

Hope this helps...

Cheers,
KV[/QUOTE]
 Why does this happen? This has happened to me twice now. I figured out the fix, but why is it happening? I'm not changing a thing? Is this a bug of some kind?

---

### Post by arjay1 on 2005-07-14
Looked like a good suggestion - clever of you to find it.  However, I ran it and still have exactly the same problem.  I looked at the thread you recommended and it is exactly the same problem as mine but the solution does not work.

Any idea how I would look at the permissions for .ICEauthority - or anything else I might try.  

Getting desperate!

---

### Post by arjay1 on 2005-07-14
IchBin - hope you picked up my post.

Did the recommended solution work for you or did you have to do anything else?

I am really annoyed - I have wasted 4 hours so far when this was not a problem of my making and I have other important things to do!!

EDIT: WHOOPS - MY APOLOGIES.  The proposed solution of chown of the .ICEautority worked fine - it was my fault - a small typo in the CLI command.

However, the fact remains that several people have had this unforced error - is it a bug or what?

---

### Post by IchBin on 2005-07-14
[QUOTE=arjay1]IchBin - hope you picked up my post.

Did the recommended solution work for you or did you have to do anything else?

I am really annoyed - I have wasted 4 hours so far when this was not a problem of my making and I have other important things to do!!

EDIT: WHOOPS - MY APOLOGIES.  The proposed solution of chown of the .ICEautority worked fine - it was my fault - a small typ in the CLI command.

However, the fact remains that several people have had this unforced error - is it a bug or what?[/QUOTE]
 You can look at the permissions by doing the following.

ls -al /home/username/,ICEauthority

It should look similar to mine.
-rwxr-xr-x 1 username username 322 2005-07-14 13:18 /home/username/.ICEauthority

If your line says root instead of username that's probably why you can't login under your other account

Of course, substitute username with your username. :)

---

### Post by arjay1 on 2005-07-14
IchBin - thanks for the info about finding authorities - very useful.. You will have seen from my post that crossed with yours - the proposed solution worked OK.  But what a WASTE of time!

---

### Post by elsewhere on 2005-07-14
[QUOTE=IchBin]Why does this happen? This has happened to me twice now. I figured out the fix, but why is it happening? I'm not changing a thing? Is this a bug of some kind?[/QUOTE]

I can't say authoritatively, but I believe it may be caused occassionally by using sudo to launch KDE or other x applications with root privileges, instead of kdesu. 

Just a theory though, I don't know for sure.

KV

---

