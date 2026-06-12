---
title: "Just installed Firefox 1.5, broke my Flash sound"
date: 2005-12-11
forum: General Help
---

### Post by grte on 2005-12-11
Okay, so I've just installed Firefox 1.5.  I had this same issue (no sound in Flash) with 1.0.7, and managed to fix it by opening up /etc/mozilla-firefox/mozilla-firefoxrc and changing FIREFOX_DSP="auto" to FIREFOX_DSP="aoss".

However, now that I've upgraded to 1.5, sound no longer works in Flash.  I've checked that same file, and it's still set as FIREFOX_DSP="aoss".

Any ideas?

---

### Post by grte on 2005-12-11
Okay, so I think I know what's wrong here.  I opened up the file for Firefox 1.07, which is still installed.

Only problem is, I don't know the filename to try the same thing for Firefox 1.5.  Can anyone help?

---

### Post by Joey French on 2005-12-11
Man, mine did the same thing. I would love to see this resolved.

---

### Post by jrib on 2005-12-11
if you read through [http://ubuntuforums.org/showthread.php?t=76743&page=2](http://ubuntuforums.org/showthread.php?t=76743&page=2) you can get a solution (it's post #19 but you also need to make the libesd.so.1 symlink which is mentioned before)

---

### Post by grte on 2005-12-11
Alright, that got my sound working.  Thank you very much.

And Joey French, to save you some looking around, I'll repeat the instructions here:

In the terminal:

```
ncampbell@naaman:~$ cd /tmp
ncampbell@naaman:/tmp$ mkdir /tmp/.esd
ncampbell@naaman:/tmp$ ln -s /tmp/.esd-1000/socket /tmp/.esd/socket
```

With thanks to naaman

And then the following, to create a startup script that'll create the previous directory:

1. Goto where startup scripts are kept:
cd /etc/init.d
2. Create a "flash-sound" script...
sudo vim flash-sound (replace vim with your choice of text editor)

3. make flash-sound contents look like:
```
#!/bin/sh
#Create symlink under /tmp for esd to get flash player working

mkdir /tmp/.esd
ln -s /tmp/.esd-1000/socket /tmp/.esd/socket
```

4. make sure your new script has the correct permissions:
sudo chmod 755 flash-sound

5. finally let the system know to execute it at startup:
sudo update-rc.d flash-sound start 51 S .
(don't miss the dot "." at the end of the line above)

With thanks to skylark

---

