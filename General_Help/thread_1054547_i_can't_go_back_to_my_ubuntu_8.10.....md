---
title: "i can't go back to my ubuntu 8.10...."
date: 2009-01-29
forum: General Help
---

### Post by redc on 2009-01-29
I used ubuntu 8.10 for 4 mouths, everything is fine. But yesturday after i install the "global menu", errors start occur, the last time i use ubuntu, the terminal doesn't response and package manager doesn't work ( I wanna unzip a file and it said there are problems with it, it said there is an error and tell me try to right click the file and select package manager again, but it still not working). The worse thing is now when i boot my ubuntu, now it just keep showing me the loading sign (normally it should be login interface) . I tried "sudo dpkg --configure -a " (thx for utnubuuser solution), unfortunatlly, after I type sudo dpkg -- configure -a, it said the following files had error:


libgtk2.0-0
gtk2.0-examples
gtk2-engines-pixbuf
gnome2-globalmenu-applet
libgtk2.0-bin


So what should I do next???

---

### Post by spcwingo on 2009-01-29
This is purely a guess but I would run:

```
sudo apt-get install --reinstall libgtk2.0-0 gtk2.0-examples gtk2-engines-pixbuf gnome2-globalmenu-applet libgtk2.0-bin
```

Like I said, this is purely a guess.  Wait for someone else more knowledgeable on this to confirm/deny before running the above command.

---

### Post by redc on 2009-01-29
Thx for your advise, I hope more people can answer my question because I really need my ubuntu back.....BTW vista real suck~~~

---

### Post by utnubuuser on 2009-01-30
Hi redc  -- been away from the comp a while,...

If you're still looking for solution...

Maybe try > sudo apt-get remove --purge libgtk2.0-commonthen 
> sudo apt-get install libgtk2.0-common

You could also follow spcwingo's suggestion.  Maybe try one at a time though.
If you look through synaptic, you'll see there are a lot of libgtkxxx.xxx.

From reading some other posts,  your desktop might be pooched.
One suggestion is to re-install gnome  
Gist of the other threads...  can't fix problem.

Here's one of the threads> [http://ubuntuforums.org/showthread.php?t=628546](http://ubuntuforums.org/showthread.php?t=628546)

Re-installing gnome might not be such a bad idea.  Maybe try installing without removing,  then, if that doesn't work, remove then re-install, and if that doesn't work,  remove --purge, then reinstall.  If you just reinstall, your configurations should be retained,  if you purge, you'll lose your custom configurations. 

How did you get global-menu?  Repository or Google or .deb file?
Some of the articles I've read suggest it should work just fine unless you're using a 64bit machine.

---

