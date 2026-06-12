---
title: "[SOLVED] Help with Conky config..."
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by tad1073 on 2008-01-09
I am having the same problem
path=home/user name/.conkyrc/conky.rc
can you help?
thanks in advanced!!!

---

### Post by notwen on 2008-01-09
What issues are you having w/ conky?  Is it not working at all?  Is it not loading a specified config file?

---

### Post by tad1073 on 2008-01-09
It works, it is just not loading the mentioned file.

---

### Post by FuturePilot on 2008-01-09
It's not supposed to be in a separate directory. Just name the file .conkyrc (note the . dot in front, that's important) and drop it in your home folder.

---

### Post by shifty2 on 2008-01-10
Is it not /home/user/.conkyrc where .conkyrc is the document, rather thant /home/user/.conkyrc/conky.rc

---

### Post by tad1073 on 2008-01-10
> **FuturePilot said:**
> It's not supposed to be in a separate directory. Just name the file .conkyrc (note the . dot in front, that's important) and drop it in your home folder.

thanks for your help, it is working now. do you know anything about the weather script, I downloaded it, put it in  
home/thomas/.scripts and that is where the code in the conkyrc file point to. It shows current weather but no stats, how do I make the weather.sh file?

---

### Post by tad1073 on 2008-01-10
> **shifty2 said:**
> Is it not /home/user/.conkyrc where .conkyrc is the document, rather thant /home/user/.conkyrc/conky.rc

thanks, I got it working.

---

### Post by rjmdomingo2003 on 2008-01-12
> **tad1073 said:**
> thanks for your help, it is working now. do you know anything about the weather script, I downloaded it, put it in  
home/thomas/.scripts and that is where the code in the conkyrc file point to. It shows current weather but no stats, how do I make the weather.sh file?
Did you make the script executable?
```
sudo chmod 755 */path/to/script*
```

---

