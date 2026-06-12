---
title: "any way to bypass having to type ./foo for executable symlinks?"
date: 2009-05-28
forum: General Help
---

### Post by alexweber15 on 2009-05-28
I created a couple symlinks to apache2 and other programs that I run on a regular basis to save me typing "sudo /etc/init.d/apache2 reload" for example.

I created a symlink in my home dir but the only way I can run it is by typing "sudo ./apache" I thought I could just go "sudo apache" but it doesn't work... is there something I'm missing here?

thanks

Alex

---

### Post by mixmaster on 2009-05-28
Can you run any program in your home directory without the leading "." ?

Unlike windows, linux does not automatically prepend the current directory to your search path.  To do what you want, you need to have your home directory explicitly set in your path

echo $PATH 

will tell you what your current path is set to.

You may do better to create the symlink in /usr/local/bin

---

### Post by Richardcavell on 2009-05-28
Should you be using an alias instead?

Richard

---

### Post by alexweber15 on 2009-05-28
> **Richardcavell said:**
> Should you be using an alias instead?

Richard

maybe??  I don't know I moved to Ubuntu from a lifetime of Windows about 2 weeks ago... it's been fun :)

but I really don't know... you tell me! ;)

btw, **mixmaster**, I moved the symlinks to /usr/local/bin and they work perfectly!  thanks!! :D

---

### Post by maheshasolkar on 2009-05-28
I tend to agree with Richardcavell. These little convenience shortcuts/scripts we write to make things faster, should always reside in our home directory (IMHO). That way, they stay around when you do a clean re-install - provided of course that you backup the home directory/or have it on a different partition.

When you do a clean install, /usr/local/bin will be refreshed and you will lose all your custom scripts.

I usually keep such scripts in ~/bin and add that path in $PATH. Or create aliases for simple stuff.

Just my 2¢.

---

### Post by tukuyomi on 2009-05-28
You can put them in a $HOME/bin folder.
If your ~/.bash_profile is OK, you can then load them without the ./
Your ~/.bash_profile OR your ~/.profile must read 
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```If you can't read this from ~/.bash_profile, simply add it at the end of the file.
If you happen to have both ~/.bash_profile and ~/.profile, ~/.profile will be ignored.

---

### Post by alexweber15 on 2009-05-28
> **maheshasolkar said:**
> I tend to agree with Richardcavell. These little convenience shortcuts/scripts we write to make things faster, should always reside in our home directory (IMHO). That way, they stay around when you do a clean re-install - provided of course that you backup the home directory/or have it on a different partition.

When you do a clean install, /usr/local/bin will be refreshed and you will lose all your custom scripts.

I usually keep such scripts in ~/bin and add that path in $PATH. Or create aliases for simple stuff.

Just my 2¢.

Thanks! :)

I followed your advice (googled aliases) made some aliases... wow this is addictive! :P

---

