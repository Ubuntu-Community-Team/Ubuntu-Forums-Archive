---
title: "Unity most used apps dissapeared"
date: 2011-06-12
forum: Desktop Environments
---

### Post by chaemil on 2011-06-12
Hi. my most used apps just dissapeared in unity dash. I've already tried to reinstall the zeitgeist or run this commands: 

"unity --reset" 

"rm ~/.local/share/zeitgeist/activity.sqlite" 

"zeitgeist-daemon --replace"
  
nothing seems to work...

---

### Post by wildmanne39 on 2011-06-12
> **chaemil said:**
> Hi. my most used apps just dissapeared in unity dash. I've already tried to reinstall the zeitgeist or run this commands: 

"unity --reset" 

"rm ~/.local/share/zeitgeist/activity.sqlite" 

"zeitgeist-daemon --replace"
  
nothing seems to work...
Hi, did you restart the system after unity reset?

---

### Post by chaemil on 2011-06-13
yes i did... it think it has something to do with the zeitgeist, but my file lense working fine it only affected the applications one.

---

### Post by wildmanne39 on 2011-06-13
> **chaemil said:**
> yes i did... it think it has something to do with the zeitgeist, but my file lense working fine it only affected the applications one.

Hi, I am not sure what is going on so I am going to bump this thread and hopefully some one can help.

---

### Post by chaemil on 2011-06-18
it wont work even if i downloaded the new version of zeitgesit from PPA. so it's something else or there is left something wrong with the zeitgeist

---

### Post by -Inoe- on 2011-08-10
It happened in my Natty too. Are there any solutions?

---

### Post by -Inoe- on 2011-09-08
I found the solution (also posted in **[AskUbuntu]("http://askubuntu.com/questions/56783/unity-dash-most-frequently-used-application-disappeared-how-to-reinstall-unity/60621#60621")**).

I got another problem with file search, and tried to completely remove and reinstall the components of unity and  zeitgeist many times but it didn't help. So, I tried something else and  found the solution.

Simply delete the **~/.local/share/zeitgeist/** folder (not only the activity.sqlite file), and restart the computer. It will generate new and fresh zeitgeist folder, and now the dash is normal again.

Note:
Just for safety reason, though, I actually chose to rename the **zeitgeist** folder to **zeitgeist.bak** instead of deleting in case it doesn't go as intended, because it actually is just a **trial and success** attempt :)

---

