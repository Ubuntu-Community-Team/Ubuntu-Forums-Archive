---
title: "gedit opens files as blank"
date: 2009-05-02
forum: General Help
---

### Post by pluMmet on 2009-05-02
I'm trying desperately to have Ubuntu 9.04 Studio with a virtulization of xp64.

It's a slow process of me muddling thru nvidia problems, mounting network drives and getting virtualbox to work.

I've been pulling my hair out for a couple of weekends now.

When I do a sudo gedit of any file it's blank.

Last weekend I had found a way to alter a file and save it without using sudo edit because as we all know when you just navigate to the file and make changes it won't let you save.

Well I can't remember what after hours of internet research last weekend I came up with to edit files and I'm damn frustrated.

My conclusion is I just need gedit to work.

Why oh why does it open files as blank?

---

### Post by Ericyzfr1 on 2009-05-02
The only time I opened a blank file w/ gedit was because I was in my /home folder not the folder where the file is located.

---

### Post by pluMmet on 2009-05-02
HEY it worked. THANKS!

is there a way to get to root filesystem right away in terminal without having to do a 'cd ..' 3 times?

---

### Post by geirha on 2009-05-02
```
cd /
```

You can also type "cd " without hitting enter, then drag the folder from nautilus over the terminal. It will fill in the full path to the folder so you can just hit enter and get straight to that folder.

EDIT:
Thirdly, there's a package called [nautilus-gksu](apt:nautilus-gksu). After installing that and logging out and back in again, you can right-click a file or folder and choose Open as administrator.

---

