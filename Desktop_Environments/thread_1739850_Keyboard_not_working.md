---
title: "Keyboard not working"
date: 2011-04-26
forum: Desktop Environments
---

### Post by jamsh on 2011-04-26
Yesterday I installed XFCE, using synaptic package manager, and I immediately had the problem of a non-working keyboard, which makes things very difficult. I can't even login!
I found an old usb mouse which means I can now navigate around the desktop, but as everything depends on being able to type in information, it doesn't really help.
So, basically I have a dead computer, can someone suggest a solution????

---

### Post by Paddy Landau on 2011-04-26
Did you install XFCE over normal Ubuntu? You don't say what version of Ubuntu you have.

When you boot, immediately press and hold the Shift key. You should get a menu instead of the normal splash screen. You can select the recovery option, and manually uninstall XFCE.
```
sudo apt-get purge xfce
```I am presuming that you originally had Gnome, and that you have not uninstalled it.

---

### Post by jamsh on 2011-04-26
Thanks for the quick reply. I've just done as you suggested and its still the same.
When I type in the code I get the following: Reading pkg lists......done
Building dependency tree
Reading state info........done
E: unable to locate package XFCE

I am using 10.10 and I did install over Ubuntu. I haven't uninstalled gnome.

---

### Post by Paddy Landau on 2011-04-26
> **jamsh said:**
> E: unable to locate package XFCE
Linux is case-sensitive. Type xfce in lower-case.

---

### Post by jamsh on 2011-04-26
Same result again in lower-case.I am typing your code into the screen which appears when I click on 'Drop to root shell prompt', is that right?

---

### Post by Copper Bezel on 2011-04-26
The package is actually xfce4, but it's a meta-package. Removing it won't actually remove all the XFCE components installed. 

Since it works in console, does your keyboard still work in Gnome?

---

### Post by jamsh on 2011-04-26
No. Not functioning at all, except in terminal.

---

### Post by Copper Bezel on 2011-04-26
And did you install xubuntu-desktop, or just xfce4? The latter shouldn't have changed your GDM (login screen) settings, but it's certainly possible. I'm thinking something's happened to your default keyboard layout in GDM.

What layout appears in the lower left at the login screen, by the way?

---

### Post by Krytarik on 2011-04-26
I assume that you are still getting the login screen of GDM, since both of the mentioned metapackages don't include XDM.

At the login screen, look to the lower right, there you will find accessibility options, make sure that "Only accept long keypresses" is *not* enabled.

---

### Post by jamsh on 2011-04-27
At the bottom of the 'login'screen, I have a little toolbar which consists of: Language, English(UK),Next to that is: Keyboard, UK and next to that is 'Session'(with Ubuntu Desktop Edition selected).Then on the right is the 'Accessibility' button and none of the options listed are checked.
I can now access the system after I created a document(on my friends laptop), with my password as the content, put this on a memory stick and loaded it to my laptop and using the usb mouse can now 'copy and paste' my password to access programs, which require authentication and also go online.But I still have a 'dead' keyboard.
Maybe I'll just wait for the new release tomorrow and I should be able to download that. This might solve my problem????

---

### Post by Paddy Landau on 2011-04-27
> **jamsh said:**
> At the bottom of the 'login'screen, I have a little toolbar which consists of: Language, English(UK),Next to that is: Keyboard, UK and next to that is 'Session'(with Ubuntu Desktop Edition selected).Then on the right is the 'Accessibility' button and none of the options listed are checked.
For *Session*, you should be able to select Gnome or Failsafe Gnome. Can you do so?

> **jamsh said:**
> Maybe I'll just wait for the new release tomorrow and I should be able to download that. This might solve my problem????
I'm sure it will, as your system did work before something happened with the XFCE installation. However, you will get the teething problems that inevitably arise in the first few weeks of a release.

---

### Post by jamsh on 2011-04-27
OK, I'll try the new release tomorrow.
Thanks a lot for all the input.

I'll report back on this thread.

---

### Post by Krytarik on 2011-04-27
Ok, I thought you can't even login, like you said. How did you manage it then, with autologin, or also with the help of the mentioned document?

Now that you are logged in to your desktop, the same accessibility option is there again, you will find it in "System -> Preferences -> Keyboard -> Accessibility (tab)", check it, too.

---

### Post by jamsh on 2011-04-28
UPDATE

Keyboard working again after 11.04 update!

Once again thanks.

---

### Post by Paddy Landau on 2011-04-28
> **jamsh said:**
> Keyboard working again after 11.04 update!
Good news.

Please mark the thread as solved.

---

### Post by Copper Bezel on 2011-04-28
If he did a fresh install of 11.04, then the problem was never identified. Marking the thread solved wouldn't be entirely accurate. (Then, implicitly, the solution for the next person to have this problem is "regret installing XFCE, then reinstall Ubuntu.")

---

### Post by prince_niceguy on 2011-05-11
> **jamsh said:**
> At the bottom of the 'login'screen, I have a little toolbar which consists of: Language, English(UK),Next to that is: Keyboard, UK and next to that is 'Session'(with Ubuntu Desktop Edition selected).Then on the right is the 'Accessibility' button and none of the options listed are checked.
I can now access the system after I created a document(on my friends laptop), with my password as the content, put this on a memory stick and loaded it to my laptop and using the usb mouse can now 'copy and paste' my password to access programs, which require authentication and also go online.But I still have a 'dead' keyboard.
Maybe I'll just wait for the new release tomorrow and I should be able to download that. This might solve my problem????

Thanks I had a similar kind of issue only gdm required long key press otherwise system was working fine. Thanks this solved the issue.

---

