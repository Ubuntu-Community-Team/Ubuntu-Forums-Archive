---
title: "Visual effects work, but no window borders!"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Honeybee on 2007-11-22
Hi everyone, 

This seems to be a common problem, and I've been through all the posts I can find about it, but I've had no luck fixing it. 

Visual effects seem to work fine, but when I enable them I lose my window borders.  However, the rest of the effects seem to work ok.

I have tried installing the compizconfig-settings-manager, and I have made sure the window borders are switched on. But I still do not get any.


I have a Radeon 9250, and I am using the open source ati drivers. 

Can anyone help me? It seems like it should be a simple problem, as the rest of the effects are working ok! :confused:

Thanks,

H

---

### Post by lomion on 2007-11-22
Have you installed emerald? I think you can solve it by setting the decorator app to emerald in the Window Decoration plugin.

---

### Post by Honeybee on 2007-11-22
I haven't, but I'll try that!

Thanks

H

---

### Post by Znort_Ubern00b on 2007-11-22
Try this in a terminal:

Code:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24


if you are using nvidia card this works

---

### Post by Honeybee on 2007-11-22
Hurrah, I now have window borders! After installing Emerald.

Now, how can I change the theme, as it doesn't seem to have any themes listed in emerald. I'm stuck with some default red title bar theme.

Anyone know?

Thanks,

H

---

### Post by lomion on 2007-11-22
install emerald-themes and go to gnome-look.org. There you'll find lots of nice themes.

---

### Post by Honeybee on 2007-11-22
Thanks, but I can't see emerald-themes.  Is it in the Gutsy universe repository? Because I can't find it.   

On the plus side, Visual effects are all now working nicely!

Cheers,

---

### Post by Roanoke on 2008-03-15
I don't see that input field on mine.

---

### Post by Zorael on 2008-03-15
The emerald-themes package isn't in the Gutsy repositories, [but you can grab it from the Feisty ones here](http://packages.ubuntu.com/feisty/emerald-themes).

The input field is the 'command' field. It starts emerald by default.

---

### Post by Roanoke on 2008-03-16
If all I needed to do was type in 'emerald', it didn't work. Effects yes, borders no.

---

### Post by Zorael on 2008-03-16
> **Roanoke said:**
> If all I needed to do was type in 'emerald', it didn't work. Effects yes, borders no.
Well, no. With the command field empty, it defaults to emerald.


Do you have Emerald (package **emerald**) installed?

What is your output from entering 'compiz --replace' in a terminal?

Nvidia/ATI?

---

### Post by Roanoke on 2008-03-16
I do have emerald.

```

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
[: 352: -lt: argument expected
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
inotify_add_watch: No such file or directory

```

NVidia.

---

### Post by Roanoke on 2008-03-16
Hey, it works! I had an extra parameter in a field. But, what does 'xgl not present' mean in the output?

How do I round window border corners in emerald?

---

### Post by Furiattl on 2008-03-18
> **Honeybee said:**
> Thanks, but I can't see emerald-themes.  Is it in the Gutsy universe repository? Because I can't find it.

It's in the synaptic.

By the way. Thanks a lot, my effects are working ok now.
Had the same issue with missing window borders.
Cool.

---

