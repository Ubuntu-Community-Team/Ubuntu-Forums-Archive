---
title: "Where is the bar?"
date: 2007-04-10
forum: Desktop Effects &amp; Customization
---

### Post by Petester on 2007-04-10
After installation of Beryl, and when i run it, the bar that has the name, minimize/maximize/close window buttons has gone. I flipped throuigh every settings in Beryl Settings manager but didnt find anything close to that..

How do i make it appera again?

---

### Post by dfreer on 2007-04-10
try installing emerald, and then Beryl-Manager > Select Window Decorator > Standard Beryl Decorator (Emerald). Then Beryl-Manager > Reload Window Decorator
If that doesn't work post what guide/methods you followed to install beryl and we can help you out from there :)

---

### Post by Petester on 2007-04-10
Thanks a lot dfreer. I wonder where can i download that?

---

### Post by PriceChild on 2007-04-10
What graphics card do you have?

Please pastebin yourx xorg.conf

---

### Post by dfreer on 2007-04-10
```
sudo apt-get install emerald emerald-themes
```
That should do the trick. Also, you should be able to use metacity as your window decorator, just choose metacity instead of emerald and then reload.

---

### Post by Petester on 2007-04-11
I selected Emerald but i stil see the problem

but out of curious, I selected Gnome for the Windows Manager and I see the bar again

How do I select the themes in Emerald Themer?

---

### Post by dfreer on 2007-04-11
In Beryl-Manager > Emerald Theme Settings :) Click on a theme and that's pretty much it.

---

### Post by Petester on 2007-04-12
No it didnt change..

I am using a 7600GT with nVidia drivers from Envy.. does that help?

---

### Post by dfreer on 2007-04-12
Try this:
(1) Go to Beryl-Manager > Select Window Decorator > GTK Window Decorator (or whatever is there besides emerald)
(2) Go to Beryl-Manager > Select Window Manager > Metacity (Gnome Window Manager)
(3) Quit Beryl-Manager (so that it is no longer running)
(4) Open two terminals and a text editor somewhere where you can see them all.
(5) In one terminal type the command *beryl* copy ALL output into text editor.
(6) After Beryl Loads (you should now have no title bars), enter the command *emerald --replace* in the other terminal. copy all output into the text editor, and note whether you have title bars or not.
(7) post all output in the text editor here, and let us know if *emerald --replace* fixed your title bars (you could see them)

---

