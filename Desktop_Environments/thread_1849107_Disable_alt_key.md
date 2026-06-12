---
title: "Disable alt key"
date: 2011-09-23
forum: Desktop Environments
---

### Post by kace91 on 2011-09-23
Hello to everyone. First of all I want to introduce myself, as this is my first post :p

I have a  problem regarding the alt key. My laptop's keyboard is broken, and that key is pressed randomly, so writing anything becomes almost impossible (each time I press a key I may trigger an alt+whatever shortcut)

I know that's a hardware problem, and as far as I know it doesnt have a solution (i tried cleaning the keyboard but it didn't work) so I want to disable every function of the alt key, as if it just weren't there. Is that posible? If so, how can I do it?

Thanks in advance!

Edit: I wasnt sure about where to make this post, if I posted it in a wrong section my apologies :P

---

### Post by LinuxFan999 on 2011-09-23
Did you try plugging in an external keyboard?

---

### Post by David Andersson on 2011-09-24
You can use xmodmap to remap the Alt key to nothing.
 
Open a terminal and type this command
```
xmodmap -pke | grep "= *Alt"
```
It will show the keycode of the current Alt key. In my case it shows
```
keycode  64 = Alt_L Meta_L Alt_L Meta_L
```
In your case the keycode (64) might be something else.

Open a text editor.

Enter this text (but replace 64 with what you got):

```
! Disable Alt key
keycode  64 = NoSymbol NoSymbol NoSymbol NoSymbol
! Enable Alt key
!keycode  64 = Alt_L Meta_L Alt_L Meta_L
```

Save with name .Xmodmap in your home folder. (The name begins with dot, so it is normally hidden. To see it innautilus, press Control H.)

To test it, in a terminal type
```
xmodmap .Xmodmap
```

Now keys should act the same wether Alt is pressed or not.

If it works, *logout and login*, and when Ubuntu asks if it should read .Xmodmap, please let it do, that is, click *.Xmodmap* in the left list and click *Add*.

If you later want to restore normal behaviour, *remove or rename* the .Xmodmap file and *logout and login*. If you want to restore normal behaviour in the current session, remove the "!" in front of the second keycode in the file, and add a "!" in front of the first, and issue the xmodmap command again.

(It may be nice to have an Alt key, so if you have an unused spare key on the keyboard, you might be able to redefine it to be a new Alt key.)

---

### Post by kace91 on 2011-09-24
Thanks! much better now... you just saved my life :p

---

