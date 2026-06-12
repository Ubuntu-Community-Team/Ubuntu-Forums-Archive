---
title: "Launcher doesn't remember icons"
date: 2011-05-12
forum: Desktop Environments
---

### Post by vaibhav on 2011-05-12
I recently upgraded from Lucid to Natty. I'm having this issue where the icons in the Launcher are not being "remembered". I always see these "LibreOffice Writer", "LibreOffice Calc", etc. icons. I don't want them, so I uncheck "Keep in Launcher" option of the corresponding icons. And also add new icons that I want, like "Terminal". But when I log out & log back in, the default icons are seen.

Please help me resolve this issue.

Thanks.
Vaibhav

---

### Post by GonZo on 2011-05-12
I've the same problem, after reboot or close session the launcher icons come back to initial state, including the ones I've removed.

---

### Post by halfak on 2011-06-11
I'm stuck with the same issue.  I just tried out gnome3 (big mistake) and finished reverting back to Unity(using ppa-purge).  As far as I can tell, this is the only issue I have left to resolve.

---

### Post by christoph411 on 2011-06-11
Doing a reset MIGHT help, but I'm doubtfull... but it's worth a try! :)

```
 unity --reset 
```

---

### Post by wildmanne39 on 2011-06-11
> **vaibhav said:**
> I recently upgraded from Lucid to Natty. I'm having this issue where the icons in the Launcher are not being "remembered". I always see these "LibreOffice Writer", "LibreOffice Calc", etc. icons. I don't want them, so I uncheck "Keep in Launcher" option of the corresponding icons. And also add new icons that I want, like "Terminal". But when I log out & log back in, the default icons are seen.

Please help me resolve this issue.

Thanks.
VaibhavHi, sometimes there is a issue with them staying in the launcher, but have you opened the program that you want in the launcher then clicked keep in launcher while the program is open? Also you can click on the power users guide in my signature it has ways of creating new launchers and a lot more.

---

### Post by yanom on 2011-06-14
> **christoph411 said:**
> Doing a reset MIGHT help, but I'm doubtfull... but it's worth a try! :)

```
 unity --reset 
```

tried it, then this happened: ```
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 85, in reset_unity_compiz_profile
    subprocess.Popen(["metacity", "--replace"]) #TODO: check if compiz is indeed running
  File "/usr/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1213, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

---

### Post by felixbur on 2011-08-11
I have the same problem: installed natty and the unity launcher does not remember the icons after reboot. libdconf0 and dconf-tools are installed.
cheers,
felix

---

### Post by Krytarik on 2011-08-11
> **felixbur said:**
> I have the same problem: installed natty and the unity launcher does not remember the icons after reboot. libdconf0 and dconf-tools are installed.

Then just reinstall "libdconf0", and then relogin.

[http://ubuntu4beginners.blogspot.com/2011/07/unity-reset-after-restart-relogin.html](http://ubuntu4beginners.blogspot.com/2011/07/unity-reset-after-restart-relogin.html)

Greetings.

---

### Post by felixbur on 2011-08-12
>Then just reinstall "libdconf0", and then relogin.

thanks!
this helped

cheers,
felix

---

