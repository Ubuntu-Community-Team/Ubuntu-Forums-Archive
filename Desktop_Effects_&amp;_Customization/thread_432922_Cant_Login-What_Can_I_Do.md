---
title: "Cant Login-What Can I Do?"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by dontgetshocked on 2007-05-04
Ok, I was using  Beryl and checked off the auto login feature and now I cant get the login screen to appear. If I use ctrl/alt/f2  then I get a text login and I tried re-doing the dpkg reconfigure thing with no success. I also tried using sudo /etc/init.d/gdm restart and it briefly showed the Beryl logo and again no login screen or desktop. I tried using the restore function and it didnt help. i cant help believe that I need to manually edit the file or something to make the desktop use metacity instead of beryl.I tried using nv and also nvidia for the graphics setting as I do have an nvidia fx 5600 card. Do I now have to re-install the whole os and lose all of my settings or what?  Suggestions, Please...

Thanks,

Dave

---

### Post by reckless2k2 on 2007-05-04
What version of Ubuntu are you using and can you get to the command line in recovery mode? I'd suggest removing beryl and backtrack from there.

---

### Post by dontgetshocked on 2007-05-04
I am using Feisty. How can I remove Beryl anyway? Shouldnt I be able to just use metacity instead of removing beryl? I know I have to edit something or input some code, just dont know what it is. Yes, I can get to thew command line but now what? I need to know what code to put in to fix this. Thanks,

Ok, I managed to uninstall beryl and still not able to login, i.e. no login screen.

---

### Post by reckless2k2 on 2007-05-06
you can try to reconfigure the x-server but it sounds like you fudged something good but i'm sure it's a simple fix though. i'm no ninja and it sounds like you might need a little more of  ninja. i know there should be a command that can kill the auto login but the auto login is not the problem.  maybe someone will chime in on this one. try posting the errors you get. 

"dmesg" without quotes at the command line.

---

### Post by kpolice on 2007-05-06
```
sudo gdmsetup
```

go to the security tab and disable auto login.

---

### Post by dontgetshocked on 2007-05-06
Thanks everyone but I got tired of messing with it and backed up all my data and re-installed.




lol

---

