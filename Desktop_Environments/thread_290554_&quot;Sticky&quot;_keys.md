---
title: "&quot;Sticky&quot; keys?"
date: 2006-11-01
forum: Desktop Environments
---

### Post by zanglang on 2006-11-01
Hi guys, I seem to have a very odd problem here.
For some reason recently I've been getting "sticky" keys alot while typing. For example, while typing under normal circumstances,

I get somethingggg just like thissssssss, wwwwhere Ubuntu tttthinks i'm holding down the keys while    i'm just hitting it once. Usually I wouuuld then have to press Backspace to delete thhhhhe keys, but i'm not ggggoing to for this post just to demmmmmonstrate. It hhhappens fffffor every key on the keyboard, including alphabets, Space, and diiiiirectional keys.

My typing speed and interval is just normal I guess, and so is my keyboard since it works fine on Windows. It's getting terribly annoying now (I've been hitting Backspace at least 5 times per sentence while typing this :()... anyone with a suggestion how to fix this?

---

### Post by CatKiller on 2006-11-01
There are accessibility options, that include settings for key repeat rate and the like, that you can get to from System -> Preferences -> Keyboard -> Accessibility.

EDIT: I've just noticed you're using Feisty. Is that related?

---

### Post by zanglang on 2006-11-01
Hmm... I don't think it has anything related to Accessibility keyboard options, because it doesn't happen everytime I boot up, only when I'm having Ubuntu running for extended periods. (Like now this post actually types out perfectly normal) Or did you mean I can sort of reduce the effect by reducing the repeat rate?

And no, it happens in Edgy as well. :-k

---

### Post by CatKiller on 2006-11-02
I don't have a solution then, I'm afraid. The only time that's happened to me, it was a manky keyboard. Toast crumbs, I think.

---

### Post by jmsbwtr on 2006-11-26
I also have the same problem, I don't think it is any of the programs I aaaaaaam using as itttttttt also happens in gdm before i have logged on. Was this ever resolved zanglang?

Thanks

*EDIT I am also using edgy and there is sometimes a lag between pressing the keys and them appearing on screen

---

### Post by zanglang on 2006-11-26
Hmm, this is pretty weird, I stopped having the problem since last week or so I think, but I don't think I've actively done anything that might've solved it. (I did install and enable SCIM around that time, mucked around with background services and a bunch of other things though...)

If you're sure it's not a dirty keyboard problem try rebooting, keep an eye on processes' CPU usage whenever it pops up, disable unnecessary stuff and so on. Hope it works for ya. :P

---

### Post by talbain on 2006-12-05
Same problem, help please, cant login.

---

### Post by zanglang on 2006-12-05
Update:
Seems to me the source of my sticky keys problems was my USB mouse! It's pretty old now, and tends to break signal alot because of its dysfunctional cable (probably wrapped or bent too much somewhere that's affecting the wires), which generates a bunch of usb-related errors on /var/log/messages, which in turn tends to interrupt the keyboard while typing, which causes the 'sticky keys' effect.

Long story short, unplugging my mouse worked for me. YMMV. :)

---

### Post by talbain on 2006-12-08
Okay, how i solved my problem:

The computer i installed edgy on was so old that i even forgot it has no acpi support in its chipset.

(Im using a USB mouse and a PS/2 keyboard)

So what i did was:

Let the machine boot and show the login screen, since i couldnt login, i pressed "Ctrl+Alt+F1" to show the console and log in.

Then:
```
sudo nano /boot/grub/menu.lst
```

and added the text in red to this line:

```
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro quiet splash [COLOR="Red"]acpi=off noacpi[/COLOR]
```

things were still kinda crazy so i went into the BIOS and changed an option (that you might or might not have) that says "USB Legacy Mode" from "Enabled" to "Disabled" and everything went smooth as silk...

But just to be ultra super sure i decided to reinstall edgy, let the cd boot (i used the alternative disk, not the live one) and press "F6" then add "acpi=off noacpi" to the end of the line so this option gets preinstalled.

I noticed that if my BIOS has "USB Legacy Mode" set to "Enable" the comp would instantly restart after pressing "Enter", so i had to disble that first and then again the installation went smoothly.

Kudos to [bsherman]("http://www.ubuntuforums.org/member.php?u=1327") for [this]("http://www.ubuntuforums.org/showpost.php?p=9953&postcount=3") post on diabling ACPI, thread [here]("http://www.ubuntuforums.org/showthread.php?t=2620&highlight=acpi").

Later on i also added the apm module as indicated in his post.

Hope this helps anyone.
Good luck.

---

