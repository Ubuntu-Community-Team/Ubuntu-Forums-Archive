---
title: "Dual monitor configuration"
date: 2008-12-19
forum: Desktop Environments
---

### Post by TheguywholikesLINUX on 2008-12-19
Hi.

I am currently trying to get a dual monitor configurration working as my current monitor is a bit small and i have a second one just like it.
I have tried plugging them both in but the resolution is a ridiculous 640 x 480 or less.
I would appreciate any help you can give me on how to set up a dual monitor configuration, and i will be willing to give you information on my screens and graphics cards, just tell me the commands i need.

Oh yeah, i am running ubuntu-studio 8.10 'ibex'.

Thanks all.

TheguywholikesLINUX

---

### Post by TheguywholikesLINUX on 2009-04-01
Oh, this is old, i did it using NVIDIA X Server Settings that you can find if you have installed restricted drivers under the admin menu.

---

### Post by super-sauce on 2009-04-01
I dont know what kind of video card you have so i dont know if this will help, but what i did (with my nvidia card) was install the proprietary drivers that ubuntu found for me, and then in the terminal run:

gksudo nvidia-settings

and configure to your heart's content.

---

### Post by Giblet5 on 2009-04-01
If you DON'T have an nvidia graphics card, you can probably achieve perfect results by editing your xorg.conf directly.

You'll need the discrete timings for both monitors first, and you'll want to add monitor definitions to your xorg.conf file.

Then you need to figure out how you want the two "screens" laid out, and which will play the primary screen role and which graphics port that monitor is hooked to.

There are loads of examples on the web for how to do this, so I'm not going to replicate them here.

You'll eventually get frustrated and give one of the monitors to your mom anyway. Ya shoulda gone for the nvidia chip...   ;o)

---

