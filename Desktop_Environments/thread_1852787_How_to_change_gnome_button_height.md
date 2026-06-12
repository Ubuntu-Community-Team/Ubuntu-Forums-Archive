---
title: "How to change gnome button height"
date: 2011-09-30
forum: Desktop Environments
---

### Post by emab on 2011-09-30
I'm using ubuntu 10.04, and I have installed a new theme. But in this theme, the height of the buttons should be a bit smaller.

How can I change the height of the buttons of ubuntu softwares?

I think there must be a default button size for every operating system, I want to change this default height.

Thanks if everyone helps me.

[IMG]http://imgup.com/image-6CD5_4E867C48.jpg[/IMG]

---

### Post by Krytarik on 2011-09-30
Usually, I only change the settings of the themes individually, but, for ease of application and your intended universality, this should work, too:

1. Create a file called ".gtkrc-2.0" at the top-level of your home directory with this content:
```
style "button" = "default"
{
    xthickness = 6
    ythickness = 4

class "GtkButton" style "button"
```
2. Change the values to your liking.

Greetings.

---

### Post by emab on 2011-10-01
> **Krytarik said:**
> Usually, I only change the settings of the themes individually, but, for ease of application and your intended universality, this should work, too:

1. Create a file called ".gtkrc-2.0" at the top-level of your home directory with this content:
```
style "button" = "default"
{
    xthickness = 6
    ythickness = 4

class "GtkButton" style "button"
```2. Change the values to your liking.

Greetings.

I did it, but it doesn't work!

---

### Post by mcduck on 2011-10-01
> **emab said:**
> I did it, but it doesn't work!

Did you log out and back again afterwards? Changes in ~/.gtkrc-2.0 only take effect at the time when you log in.

Anyway, if it still doesn't work your only option is to do exactly the same change, but directly in the gtkrc file of the theme you are using.

---

### Post by emab on 2011-10-01
> **mcduck said:**
> Did you log out and back again afterwards? Changes in ~/.gtkrc-2.0 only take effect at the time when you log in.

Anyway, if it still doesn't work your only option is to do exactly the same change, but directly in the gtkrc file of the theme you are using.


Thank you, the secound solution worked!;)

---

