---
title: "I deleted the Examples file under ~ in kubuntu"
date: 2006-08-21
forum: Desktop Environments
---

### Post by utab on 2006-08-21
Dear all;

I deleted the Examples file under ~ in kubuntu by mistake. Is that a problem, and may I retrieve that file.

Regards

---

### Post by chaosgeisterchen on 2006-08-21
Firstly it's a directory. Deleting it won't do your system any harm but retrieving it.. I dunnot know where they can be downloaded from but there is certainly a mirror providing them.

---

### Post by utab on 2006-08-21
> **chaosgeisterchen said:**
> Firstly it's a directory. Deleting it won't do your system any harm but retrieving it.. I dunnot know where they can be downloaded from but there is certainly a mirror providing them.

Can you send yours to me?

---

### Post by encompass on 2006-08-21
Why do you want them...
jsut booth you live cd and copy them to you drive... or they might be there when you open the cd with gnome.
You may just delete the link too.

---

### Post by zba78 on 2006-08-21
It's not needed at all (I've deleted mine). if you want it back just re-install the package called example-content ```
apt-get install example-content
```

a description of it can be found at [https://wiki.ubuntu.com/ExampleContent](https://wiki.ubuntu.com/ExampleContent)

---

### Post by chaosgeisterchen on 2006-08-21
So you see.. retrieving is easy ^^

I forgot about the livecd

---

### Post by utab on 2006-08-21
> **zba78 said:**
> It's not needed at all (I've deleted mine). if you want it back just re-install the package called example-content ```
apt-get install example-content
```

a description of it can be found at [https://wiki.ubuntu.com/ExampleContent](https://wiki.ubuntu.com/ExampleContent)

No packages installed the output is

sudo apt-get install example-content
Reading package lists... Done
Building dependency tree... Done
example-content is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by utab on 2006-08-21
> **chaosgeisterchen said:**
> So you see.. retrieving is easy ^^

I forgot about the livecd

I do not have a live CD now so I have to find another way.

---

### Post by Jucato on 2006-08-21
It's probably not deleted yet. The example-content in the ~ (home) directory is actually just a symlink. The real directory is in /usr/share/example-content.

---

### Post by utab on 2006-08-21
> **Fenyx said:**
> It's probably not deleted yet. The example-content in the ~ (home) directory is actually just a symlink. The real directory is in /usr/share/example-content.

So the solution is:

ln -s /usr/share/example-content Examples

---

