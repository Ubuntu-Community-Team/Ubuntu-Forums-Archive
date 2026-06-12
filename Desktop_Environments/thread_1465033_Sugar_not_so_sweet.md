---
title: "Sugar not so sweet"
date: 2010-04-29
forum: Desktop Environments
---

### Post by Thorney on 2010-04-29
I installed the sugar-session in on up to date ubuntu 10.04 64bit laptop today. It worked okay, the emulation thing was working well. Only minor point was it seemed to cease control of my wireless and connect to long forgotten networks when I tried to set up a mesh. 

My issue however is it broke my gnome-session! I can login with gnome failsafe or xfce but gnome is broken!

To clarify 'broken' - I can login, I can start programs but the mouse doesn't click on windows - meaning I can't click any buttons, change tabs, click on search bars... use my computer.

So I promptly removed sugar and was surprised to find gnome still broken. I could login with failsafe gnome but not knowing how to fix it I wanted the internet - xfce session still runs fine and has NetworkManager hence I'm using that to write this message. Anyone got any ideas?

Before I removed sugar I noted that at GDM when I selected Sugar the screen went blank, flashed the nvidia logo then selected gnome again. So clearly something is preventing me from using the session from GDM. Although that would be an interesting problem to solve first I'd like my Ubuntu Desktop back!

---

### Post by Thorney on 2010-04-29
Hmm I tried removing everything with sugar in the name completely including settings files etc - still can't click properly.

I am now in gnome though - I found if I hold the shift key down I can click...

When I don't press the shift key and I click the mouse it tries to drag the whole window as if I had clicked on the title bar.

This is strange, and less than optimal.

I'll try reset gnome session's settings by deleting the .gnome2 folder...

Nope that didn't work either.

Any ideas?

---

### Post by Thorney on 2010-04-29
Well I created a new user account - and it is fine...

So I guess it must be something in my profile. I'll try deleting hidden configuration files from my home dir and logging back in until I find it.

---

### Post by Thorney on 2010-04-29
Well I deleted the ~/.gconf dir and all is well. Have lost all my applets, settings, passwords, mounted drives etc but at least I can now click on things.

Hope this helps someone in the future, I know I'll be testing sugar under a test user account from now on - and maybe inside a virtual machine!

---

### Post by km0r3 on 2010-05-13
It would be nice if you could upstream this bug to Launchpad to the Ubuntu Sugar Remix team. [https://launchpad.net/usr](https://launchpad.net/usr)

Thanks.

---

### Post by moiesk on 2010-07-15
You don't need to delete the whole .gconf folder, edit the file ```
.gconf/apps/metacity/general/%gconf.xml
```

delete the tag with name "mouse_button_modifier", in my case this 3 lines:

```

<entry name="mouse_button_modifier" mtime="1279125807" type="string">
    <stringvalue>disabled</stringvalue>
</entry>

```

and that's it.

---

