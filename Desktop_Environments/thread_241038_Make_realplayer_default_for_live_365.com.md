---
title: "Make realplayer default for live 365.com"
date: 2006-08-21
forum: Desktop Environments
---

### Post by oneup on 2006-08-21
I like to listen to live 365 .com radio but I loath rhythmbox and want realplayer to be default,can anyone tell me how to do this please !

---

### Post by halitech on 2006-08-22
when I went to bring it up, it gave me the standard open or save box and if you select realplayer and then do this automatically from now on, it should open everytime in realplayer

---

### Post by oneup on 2006-08-23
> **halitech said:**
> when I went to bring it up, it gave me the standard open or save box and if you select realplayer and then do this automatically from now on, it should open everytime in realplayer

When I go to box it only offers me rhythmbox or other ,no way to specify RealPlayer

---

### Post by mrgnash on 2006-08-23
> **oneup said:**
> I like to listen to live 365 .com radio but I loath rhythmbox and want realplayer to be default,can anyone tell me how to do this please !

Are you using Firefox to access live365.com? If so, then enter the following into the url bar:

```
about:config
```

... and hit enter.

Right click on an empty space in the new tab/window that appears, and select **new**>**string**. In the dialogue box that appears enter the following:

```
network.protocol-handler.app.ram
```

Not being a 365 user myself, I don't know if ram is the streaming format they actually use... if not, then substitude the appropriate format in place of 'ram.' Next, it should as you for a 'value;' so, simply type in ```
realplay
```.

Next, right click on an empty space again, and select **new**>**boolean**, and enter the following:

```
network.protocol-handler.external.ram
```

This time, the value we want is 'true.'

Hopefully that works, if not then I'm sure there'll be a tutorial/howto around here somewhere.

---

