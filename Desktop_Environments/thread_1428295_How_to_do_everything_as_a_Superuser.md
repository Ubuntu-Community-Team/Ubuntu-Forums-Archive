---
title: "How to do everything as a Superuser?"
date: 2010-03-12
forum: Desktop Environments
---

### Post by draperdt on 2010-03-12
Hi,

I am trying to use ubuntu for web development purposes. Its a local test environment and my common activities include editing php files, testing on local apache server, ftp files to server, download files from ftp etc.

I think I am missing something obvious, but can I be a superuser in the graphical environment. Such as, I open a file using gedit or kate text editor using "menu bar" or by "clicking it" and it naturally lets me edit the files without bothering me for permissions everytime. Or with ftp client, if I want to download something from my server using filezilla from the menu, it would automatically do it since it knows it me?

I know I can invoke sudo instance of programs from terminal. I was wondering of a way to do everything as superuser, every time.

Thank you.

Also, can someone suggest me their fav texteditor, I am using bluefish and I am satisfied so far.

---

### Post by snowpine on 2010-03-12
Yes, you can use 'gksu' (if you're using Gnome) or 'kdesu' (KDE) for graphical apps.

For example:

```
gksu gedit /some/random/file
```

Hope that helps. :)

---

### Post by sisco311 on 2010-03-12
Why don't you store your site(s) in your home directory, so you can edit the files without root privileges?
[uhelp]community/ApacheMySQLPHP#Virtual%20Hosts[/uhelp]

---

### Post by 2hot6ft2 on 2010-03-12
People ask on a regular basis how to "run as root all the time" and it is highly discouraged. If I were to tell you the Mods would shoot me. It's that taboo.

The answer is out there but you wont find it by asking. Sorry but I can't help in your endeavour.

---

### Post by lisati on 2010-03-12
There's always the information at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 2hot6ft2 on 2010-03-12
> **lisati said:**
> There's always the information at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
LOL, guess that answers it.

---

### Post by pastalavista on 2010-03-12
Are you wanting to defeat the main security advantage of Ubuntu and make it more like Windows?

Use sudo and gksudo as much as you want. Your system will check every 15 minutes or so to make sure you're still you and not some hacker who has knocked you out or a spybot hiding in some website you come in contact with.

I, personally, am very thankful for that.

---

### Post by draperdt on 2010-03-12
Thanks everyone. I understand the pitfalls and I will try to find my way around this issue. Its just that I instinctively try to edit the files using graphical editor and only to realize that I dont have permissions when saving. Or when I fire up ftp client to make a back up to realize I have to do all over again as gksudo.... I guess I am just not used to the workflow, but I promise I will get there.

---

### Post by kerry_s on 2010-03-12
> **draperdt said:**
> Thanks everyone. I understand the pitfalls and I will try to find my way around this issue. Its just that I instinctively try to edit the files using graphical editor and only to realize that I dont have permissions when saving. Or when I fire up ftp client to make a back up to realize I have to do all over again as gksudo.... I guess I am just not used to the workflow, but I promise I will get there.

just make a root file manager launcher & use that.

---

### Post by asmoore82 on 2010-03-12
You should definitely [COLOR="Red"]_***[SIZE="2"]not[/SIZE]***_[/COLOR] edit the files as root all the time.

You should give your regular user account permission to work with the files.

Either assign ownership to your account or maybe even better to assign group ownership
to some group like "wwwmods" and give make your account a member of that group.

---

