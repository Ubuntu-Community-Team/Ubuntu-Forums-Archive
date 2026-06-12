---
title: "X11 file is blank"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Sp@z on 2005-12-27
Ok I know I did it but I dunno how. I installed new Nvidia drivers lastnight, ran a few games played well, went to bed fired up XP today because I am lame like that and then tried to load Ubuntu, xser wouldn't load, booted into recovery mode, still didn't load, booted into 386 kernal (I am 686 now) opened up the /etc/X11xorg.config file to see that is is BLANK! (Blank in 686 too) I would laugh cause it is kinda funny but I am too tired. Tried to restore the back up of the file I made and it says it didn't exsist. Any way to restore it? Without reinstalling? Can I copy and past one I find on here? (havent looked for one yet though. Thanks.

---

### Post by 23meg on 2005-12-27
The exact name of the file is /etc/X11/xorg.conf ; if you got that wrong (mind the capitalization) you'll be seeing a blank file in your text editor.

To rebuild it you'd have to do ```
sudo dpkg-reconfigure xserver-xorg
```.

---

### Post by Sp@z on 2005-12-27
I treid that as well sorry i didn't mention it thouhg, that is when it told me it didnt exsist. :( I will try it again and triple check the punctuation :)

Edit: tried it again, said it is "broken or not fully installed"

he he he I broke Ubuntu!!! j/k not really funny, lack of sleep LOL.

---

### Post by 23meg on 2005-12-27
Please copy and paste the exact error you're getting.

---

### Post by Sp@z on 2005-12-27
I can't copy an paste the exact lines. Inorder for me to post here I need to reboot into windows, therefore the clipboard is emptied. but here are the steps I use.
At startup error:
Xserver failed to start would you like to view the logs to try and fix the problem?

I select:
yes

then it gives me stuff I really don't understand.

then it will load up the command line

I enter my user and pw and type in

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
this tries to reinstall the back up file I made, then it errors out and says the file is not found or doesn't exsist.

Then I try:
sudo dpkg-reconfigure xserver-xorg 

error says:

 the xorg file cannot be reconfigured because it is broken or not fully installed.

This is from memory and it is the best I can reproduce for you. I appreciate all the help I can get, I am trying to avoid a reinstall.

I know that I am typing it correctly since I am not getting "Command not found" errors and others of the like.

---

### Post by art on 2005-12-27
You know about tab completion when typing in command line right? So when you are typing  

sudo cp /etc/X11/

and hit tab twice, what options do you get? is there a file xorg.conf_backup? Maybe you named it differently?

---

### Post by Sp@z on 2005-12-27
I was not aware of this TAB function I will try it right now. :)

well I was able to get the file back in place. It is no longer blank. The tab function showed the backups and the correct names but they would not go back to the original conffig. But it lead me to getting the newest xserver which in turn rewrote the file and but when trying to reconfig it it still threw the message "File is broken or not fully installed" Blah I am just going to reinstall. I could have been done and running linux again by now. Thanx for the suggestions though :)

---

