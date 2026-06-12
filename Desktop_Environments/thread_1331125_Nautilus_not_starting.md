---
title: "Nautilus not starting"
date: 2009-11-19
forum: Desktop Environments
---

### Post by AliSajidImami on 2009-11-19
Hello everyone.
Recently i installed Karmic on my pc.
Its been giving some troubles on and off, but yesterday a file window stuck. i had to do some work so i killed nautilus from the system monitor. when i restarted however, the gui has no panels and it gave error that nautilus can't load my home directory, and it can't read my configuration files.
What should i do?

---

### Post by ilil on 2009-11-19
Can you run Nautilus in terminal and paste here the output (with all errors)?

---

### Post by AliSajidImami on 2009-11-19
I can't access anything in the GUI. there are no panels etcetra. I'll try running it in terminal though.

---

### Post by AliSajidImami on 2009-11-22
I tried starting it, but i can't access the terminal emulator and don't know how to put up the display in  the terminal
But here is what happens when i turn my pc on.
When i log in, First this appears
[IMG]http://ubuntuforums.org/[IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen1.jpg[/IMG][IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen1.jpg[/IMG]
then this appears
[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://i783.photobucket.com/albums/yy117/AliSajidImami/screen2.jpg%5B/IMG%5D[/IMG][IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen2.jpg[/IMG]
then this screen appears
[IMG]http://ubuntuforums.org/[IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen3.jpg[/IMG][IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen3.jpg[/IMG]
and finally me desktop appears, but it doesn't have the wall paper i had selected, or any panels and my shortcuts don't work
[IMG]http://ubuntuforums.org/[IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen4.jpg[/IMG][IMG]http://i783.photobucket.com/albums/yy117/AliSajidImami/screen4.jpg[/IMG]
I don't know how to fix it, except that i killed nautilus when it was not responding

---

### Post by emigrant on 2009-11-22
[LIST=1]
[*]press alt+f2
[*]type nautilus
[/LIST]

---

### Post by emigrant on 2009-11-22
can you log in through other user accounts?

---

### Post by AliSajidImami on 2009-11-22
I don't have any other accounts. I'll try that.

---

### Post by AliSajidImami on 2009-11-22
Okay, i created a new user in command line, and i can log in as him. but he is not in sudoers and since i have no access to the file, i can't do anything with that. Any other suggestion?

---

### Post by AliSajidImami on 2009-11-22
Now when i logged in, i accessed my original account without a hitch :D
Now, can somebody explain what happened?:confused:

---

### Post by emigrant on 2009-11-22
it may be effected by a jinn :D

---

### Post by AliSajidImami on 2009-11-22
Probably. :-D
The windows jinn who doesn't want me using linux? :-)

---

### Post by HeadHunter00 on 2009-11-22
to open terminal use ctrl+alt+f2

---

### Post by HeadHunter00 on 2009-11-22
Maybe you should install kubuntu. Sorry man, its the only possible way I can think of. Open terminal and type in "sudo apt-get install kubuntu-desktop", reboot, change session to kde and log in

---

### Post by AliSajidImami on 2009-11-23
Thanks for everything guys, but my problem is now solved. I'm changing it to "solved", but i'd appreciate if someone explained what had caused it in the first place.

---

### Post by Keesdejong on 2009-11-24
> **AliSajidImami said:**
> Thanks for everything guys, but my problem is now solved. I'm changing it to "solved", but i'd appreciate if someone explained what had caused it in the first place.

Would you mind telling us what exactly solved the problem? You should always do that, otherwise there won't be much use of this topic ;)

A friend of mine has the same problem, I can only troubleshoot trough SSH. But I managed to get an error output of Nautilus (check the output below). 

```
gosse@Ubuntu:~$ nautilus

(nautilus:2311): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2311): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2311): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2311): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentatiefout
```The machine is running Ubuntu 9.10 32 bit and is up2date.

---

### Post by fancypiper on 2009-11-24
I believe you can restore the defaults by deleting /home/<user>/.gconf/apps/nautilus

---

### Post by AliSajidImami on 2009-11-25
What i did was create a new user in terminal.
I then logged in using that user, and after that i switched to my normal account and it loaded without a hitch.
I restarted the pc and logged in using my normal login and all was fine, and i deleted the additional account.

---

### Post by ilil on 2009-11-26
to Keesdejong
I think that is the bug described [here](http://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234) and [here](http://bugzilla.gnome.org/show_bug.cgi?id=598918)

---

### Post by Keesdejong on 2009-11-29
I haven't heard any feedback from that guy, so that could only mean two things, it's either fixed or he removed Ubuntu. Anyway thanks for the replies!

---

