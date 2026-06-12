---
title: "extract ubuntu 10.10 human theme packages"
date: 2016-01-03
forum: Desktop Environments
---

### Post by zanetto on 2016-01-03
human theme

I'm using ubuntu 10.10, I tried ubuntu 14 mate, I would like to have the same desktop as in ubuntu 10 (human theme) so I copied directories /usr/share/themes and icons and wallpapers from ubuntu 10 to ubuntu mate 14 but while copying I received the error message: too many symbolic links
I would like to know how to extract human theme package from ubuntu 10.10 dvd and install in ubuntu mate 14

thank you

---

### Post by Dennis N on 2016-01-03
You could install **legacyhuman-theme** from the repositories. I think it's the same as the old human theme. Also in the repository is the **human icon theme**. Both work fine in Ubuntu MATE 14.04.

---

### Post by Bucky Ball on 2016-01-03
Always check the repositories. You can save yourself a lot of time. 'Human' is alive and well.

Attempting to copy any software from such an old release to a new one is likely to be fraught with problems.

---

### Post by zanetto on 2016-01-05
> **Dennis N said:**
> You could install **legacyhuman-theme** from the repositories. I think it's the same as the old human theme. Also in the repository is the **human icon theme**. Both work fine in Ubuntu MATE 14.04.


no, different

> **Bucky Ball said:**
> Always check the repositories. You can save yourself a lot of time. 'Human' is alive and well.

Attempting to copy any software from such an old release to a new one is likely to be fraught with problems.

no problems

do you know how to find and copy a certain package from an ubuntu dvd?

My English is bad
I try to explain better
I need to copy human theme packages from Ubuntu 10.10 dvd

How can I do?

Please, answer this question, do not write everything you have in mind

---

### Post by Bucky Ball on 2016-01-05
Why would you want to? Just install a supported release and install the Human theme from the repos. :)

If you are asking how do you find and copy any package from a Ubuntu dvd generally, please start another thread as that has nothing to do with the support request you've raised here. If you are actually asking how do you find and copy the Human theme from the 10.10 DVD so you can use it in a supported release, again, installing anything from an unsupported release and attempting to add it to a supported one is probably creating a rod for your back.

---

### Post by zanetto on 2016-01-05
On Mate support forum they told me that install human theme package taken from ubuntu 10 in ubuntu mate 14 works, no problems

My problem is how to search human theme package

Is there anybody who knows this thing?

---

### Post by Dennis N on 2016-01-05
You are right that the legacy human theme is not quite the same - darker window border and different window buttons. I looked at the Human theme on Ubuntu 8.04 (I don't have access to a 10.10) and compared it to Human-Clearlooks in Ubuntu MATE 14.04. I made screenshots, first Human theme taken on Ubuntu 8.04 and second is Human-Clearlooks taken on Ubuntu MATE 14.04. Good enough?

I also tried the human theme from Ubuntu 8.04 in Ubuntu MATE 14.04 and it doesn't work well - there is a warning that the needed theme engine "ubuntulooks" is missing, so I don't recommend it. I judge Human-Clearlooks in Ubuntu MATE nearly identical to the original Human in 8.04.

If you really want to use the theme out of 10.10, copy the human theme folder from /usr/share/themes to the same location in Ubuntu MATE. Then it will show up in the Appearance window.

---

### Post by zanetto on 2016-01-05
As I wrote copying all themes directory from ubuntu 10 to ubuntu mate 14 you have the error messages too many symbolic links

I'm looking for the way to copy from ubuntu 10 dvd the package human theme so that there is no errors

---

### Post by Dennis N on 2016-01-05
> **zanetto said:**
> As I wrote copying all themes directory from ubuntu 10 to ubuntu mate 14 you have the error messages too many symbolic links

I'm looking for the way to copy from ubuntu 10 dvd the package human theme so that there is no errors

You need to copy only one folder from the /usr/share/themes directory on Ubuntu 10.10, not all of them. Copy the folder named **Human**. I don't know exactly how you are doing the transfer, but if using a flash drive, I would copy the folder first to the Desktop on Ubuntu MATE, then use terminal commands to copy again to /usr/share/themes. That's because you need root privileges to copy into that location.

If you do it that way, then In Ubuntu MATE terminal:

```
cd Desktop
sudo cp -r Human /usr/share/themes
```

Let us know how it looks.

---

