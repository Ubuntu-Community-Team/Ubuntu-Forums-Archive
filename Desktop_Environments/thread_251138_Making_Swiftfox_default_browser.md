---
title: "Making Swiftfox default browser"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Marantz on 2006-09-05
Here is my question, hear me out before you start throwing answers around.

I have searched these forums for all of the answers to my other questions, and have found it a very useful place. Now I have a question that I cannot find an answer to.

I'm a run box whore, I'll be honest. My last two keyboard the windows key and the R key wore off because I used them so much. I was in love. I mapped it to the launch box in KDE and I have been running away, but I ran into a problem.

When I type a URL into the box, though Swiftfox is set as my default browser(ish) it won't run the URL I put in. Instead Konqueror does. *gag*

I have nothing really against Konqueror except for a few things, such as gmail does not work well with it, and sometimes videos wont play and websites won't show up correctly.

Is there any way to set it so that when I enter a URL into the launch box it launches it in Swiftfox instead of typing firefox in front of every URL I want opened with it? ](*,)

---

### Post by Marantz on 2006-09-06
Really hate to do this... *bump bump* :-\ still no reply...

---

### Post by rickg on 2006-09-06
System > Preferences > Preferred Applications...

---

### Post by Marantz on 2006-09-06
> **rickg said:**
> System > Preferences > Preferred Applications...

Did I mention I'm using KDE? And that doesnt exist?

---

### Post by rev on 2006-10-07
> 1. Open a shell
2. Run "sudo update-alternatives --list x-www-browser". You should see a list of availible browsers.
3. Run "sudo update-alternatives --set x-www-browser /usr/bin/firefox" to select Firefox as the default browser.
HTH. Thanks to martin_d!
[http://www.ubuntuforums.org/showpost.php?p=1490948&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1490948&postcount=11")

---

