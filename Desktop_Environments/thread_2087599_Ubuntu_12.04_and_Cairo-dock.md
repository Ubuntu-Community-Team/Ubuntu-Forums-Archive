---
title: "Ubuntu 12.04 and Cairo-dock"
date: 2012-11-24
forum: Desktop Environments
---

### Post by czgirb on 2012-11-24
On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)
Three option to choose.
But no matter what I choose (exclude GNOME+No Effect)
I still able to see the hidden Unity.
Is it normal? How can I turn-off the Unity?
Please guide me.

---

### Post by makitso on 2012-11-24
IMO Unity on 12.04 does not work well with any dock including Cairo.  If you auto hide Unity, it pops open all the time with any desktop object movement.  For this reason, I switched to the gnome 3 shell.  But, 12.10 behavior of Unity is better and should work with Cairo much better.

---

### Post by zombifier25 on 2012-11-24
It is a bug somehow, because my Cairo Dock installation works fine, with no Unity bar. If possible, try disabling Unity in compizconfig-settings-manager

---

### Post by czgirb on 2012-11-30
> **zombifier25 said:**
> It is a bug somehow, because my Cairo Dock installation works fine, with no Unity bar. If possible, try disabling Unity in compizconfig-settings-manager

OK! Thank you very much for the guidance.
Previously, when I first install **Cairo-dock**, in default mode, when I minimized the opened windows, it will be minimized to dock with the same apps icon. Now, since I modified the theme, the minimized windows will be minimized to Unity, instead on dock. How can make the minimized windows back to dock? What setting that I should set?
[B]Please do a favor by guiding me how to do that.
Thank you.[/B]

---

### Post by czgirb on 2012-12-01
Please help ...............

---

### Post by cybergalvez on 2012-12-01
> **czgirb said:**
> Please help ...............

it sounds like you have logged into * Cairo-Dock (with Unity Panel). As was alrady mentioned I would not run cairo and unity I don't think they play nicely together. I would either run Cairo as the session manager (one of the first two selections) or as I do with gnome-shell where it works guite nicely

---

### Post by czgirb on 2012-12-02
> **cybergalvez said:**
> it sounds like you have logged into * Cairo-Dock (with Unity Panel). As was alrady mentioned I would not run cairo and unity I don't think they play nicely together. I would either run Cairo as the session manager (one of the first two selections) or as I do with gnome-shell where it works guite nicely
On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)
Three option to choose.
But **no matter what I choose** (exclude GNOME+No Effect)
I still able to see the hidden Unity.
Is it normal? How can I turn-off the Unity?
Please guide me.

---

### Post by Krytarik on 2012-12-02
> **czgirb said:**
> On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)
Three option to choose.
But **no matter what I choose** (exclude GNOME+No Effect)
I still able to see the hidden Unity.
Is it normal? How can I **turn-off the Unity**?
Please guide me.
Well, *zombifier25* already told you that a week ago, maybe you wanna try that now, finally:
> **zombifier25 said:**
> ...try **disabling Unity** in compizconfig-settings-manager
Regards.

---

### Post by czgirb on 2012-12-03
> **Krytarik said:**
> Well, *zombifier25* already told you that a week ago, maybe you wanna try that now, finally:

Regards.

Yup! I wish to do that.
But after I do that, I unable to recognized which is IS.
**Example:** Firefox, I opened 3-windows ... **main, library**, and **download** windows.
In default settings, I will had 3 firefox icon on dock.
But now, in dock I had 1 icon only not three (default).
So I wish to set current theme to default settings.
But I don't know how to do that.

---

### Post by Krytarik on 2012-12-03
> **czgirb said:**
> Yup! I wish to do that.
But after I do that, I unable to recognized which is IS.
**Example:** Firefox, I opened 3-windows ... **main, library**, and **download** windows.
In default settings, I will had 3 firefox icon on dock.
But now, in dock I had 1 icon only not three (default).
So, now, the question is not anymore how to disable Unity in the Cairo-Dock sessions, but how to get Cairo-Dock to behave like what you say is the default, right?

---

### Post by czgirb on 2012-12-04
> **Krytarik said:**
> So, now, the question is not anymore how to disable Unity in the Cairo-Dock sessions, but how to get Cairo-Dock to behave like what you say is the default, right?

Bingo!
**The other question is:**
How can I still have **6-digital clock** and able to see it everytime I wants. Cos if I disabled the Unity. It'll caused the Top Panel to be disappeared also.
In order to distinguished a file, in file's name, I often put **6-digital clock** behind. So I know when the file was updated.

---

### Post by Krytarik on 2012-12-04
> **czgirb said:**
> Cos if I disabled the Unity. It'll caused the Top Panel to be disappeared also.
If you want the Unity Panel without the Unity Launcher, that's what the bold-marked session is for, it's using the Unity *2D* Panel:
> **czgirb said:**
> On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
** * Cairo-Dock (with Unity Panel)**
Three option to choose.

---

### Post by czgirb on 2012-12-04
> **Krytarik said:**
> If you want the Unity Panel without the Unity Launcher, that's what the bold-marked session is for, it's using the Unity *2D* Panel:
As I said in the **1st thread**:
> On a login screen there is:
[B]* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)[/B]
Three option to choose.
But no matter what I choose (exclude GNOME+No Effect)
I still able to see the **Unity**.
If you said it was called the **launcher** ... OK! I do not want to see the **launcher** ... I just wants **panel** only.
Please guide me ....

---

### Post by Krytarik on 2012-12-04
> **czgirb said:**
> If you said it was called the **launcher** ... OK! I do not want to see the **launcher** ... I just wants **panel** only.
Please guide me ....
Should I just repeat my previous post now!? :P

---

### Post by graphius on 2012-12-04
I really don't want to stir things up, but the pain of Unity and Cairo Dock is one of the things that sent me to Mint. 

Another option that *may* work for you is to install XFCE and remove unity. A guide is at [psychocats.net]("http://psychocats.net/ubuntu/purexubuntu"). This option is not quite as pretty though...

---

### Post by czgirb on 2012-12-07
> **Krytarik said:**
> Should I just repeat my previous post now!? :P

Dear Mr. Krytarik:
> On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)
Three option to choose.
But **NO MATTER** what session I choose (exclude GNOME+No Effect)
I still able to see the Unity.
Please pay an attention to the **BOLD** mark

---

### Post by czgirb on 2012-12-07
> **graphius said:**
> I really don't want to stir things up, but the pain of Unity and Cairo Dock is one of the things that sent me to Mint. 

Another option that *may* work for you is to install XFCE and remove unity. A guide is at [psychocats.net]("http://psychocats.net/ubuntu/purexubuntu"). This option is not quite as pretty though...

Dear Mr. Graphius,
If I install XFCE and removes the Unity, what will my desktop looks like? Where can I learn more about XFCE? Please show me ...

---

### Post by Krytarik on 2012-12-08
> **czgirb said:**
> Dear Mr. Krytarik:
> On a login screen there is:
* Cairo-Dock (GNOME+Effect)
* Cairo-Dock (GNOME+No Effect)
* Cairo-Dock (with Unity Panel)
Three option to choose.
But **NO MATTER** what session I choose (exclude GNOME+No Effect)
I still able to see the Unity.Please pay an attention to the **BOLD** mark
You know, I'm not going to run in circles with you ;-) :
> **czgirb said:**
> [QUOTE=Krytarik;12386294]So, now, the question is not anymore how to disable Unity in the Cairo-Dock sessions, but how to get Cairo-Dock to behave like what you say is the default, right?
Bingo!
... Cos if I disabled the Unity. It'll caused the Top Panel to be disappeared also.[/QUOTE]

---

