---
title: "path Issues.... Help Needed"
date: 2008-12-20
forum: General Help
---

### Post by brijith on 2008-12-20
Hai Friends,

I used to develop simple GUI based utilities using Python and pygtk. I also made a installation script. What it does is copy the files to a directory named **share** under **home** directory and create a bash file to invoke my application and put it in **bin** directory under **Home**. Then I had to add this new bin directory path to Path environment 
variable. For that I added 


```

if [ -d ~/bin ]; then
	PATH="~/bin:${PATH}"
fi

```

in my ~/.bashrc file

There after I could run the application as if any other command through terminal. But I can't get it thorough **Alt + F2** Run application window. Also when I create luncher giving just the command it won't work I had to use absolute path to get it work. 


How to solve this issue ? 
Please Help Me


**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

### Post by cdtech on 2008-12-20
If you enter this into your terminal:
```
bash --login
```
can you execute?

---

### Post by RealPSL on 2008-12-20
~/.bashrc is only going to be called when you launch a new bash shell. ATL+F2 is not launching a new shell. You would be better served adding those lines to your ~/.profile. After adding the lines log off and log in. You should now be able to run any program in the ~/bin path.

---

### Post by brijith on 2008-12-21
> **RealPSL said:**
> ~/.bashrc is only going to be called when you launch a new bash shell. ATL+F2 is not launching a new shell. You would be better served adding those lines to your ~/.profile. After adding the lines log off and log in. You should now be able to run any program in the ~/bin path.


Thanks for Your response. 


I am Using Debian.In my home directory I can't find a file like **~/.profile**. I can see files like **.bash_aliases, .bash_functions, .bash_history, .bash_logout, .bash_profile, .bashrc** I think .bash_profile will also run only when we run bash



[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

