---
title: "Winodw Tops disapering"
date: 2007-12-25
forum: Desktop Effects &amp; Customization
---

### Post by Tanjer1588 on 2007-12-25
Ok so i installed CGWD and got a theme for the emerald window decorator. I looked up how to change what decorater you use, emerald or gnome. So what i found told me in order to switch just type
```
emerald --replace

and

gtk-window-decorator --replace

to get back to the gnome one
```

but when i typed it it, it worked right, but in the terminal my curror drops down to an empty feild insted of showing the user@user~desktop$ thing... so i hit Ctrl+C to stop and then my window bars are gone... works the same with Emerald and the GTK one, 
```
sean@sean-desktop:~$ emerald --replace

sean@sean-desktop:~$ 

```

the empty filed is where my cursor drops to and the window takes affect but then i hit CTRL+C and it gosaway

thank you

---

### Post by Tanjer1588 on 2007-12-25
Didnt really find out why it did it but a hard restart seemed to set everything back ok, i have the emerald theme running fine now. but if anyone knows why this dose this i wold love to know

---

### Post by Forlong on 2007-12-25
That's normal. The program runs in the terminal (otherwise you won't get any outputs), so if you close it, it will terminate the application with it.

Use the command(s) via [Alt]+[F2] to prevent this.

---

