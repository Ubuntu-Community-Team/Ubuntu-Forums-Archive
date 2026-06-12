---
title: "No &quot;Advanced Desktop Settings&quot;!"
date: 2009-02-05
forum: General Help
---

### Post by photon_man62 on 2009-02-05
Hello. I saw some instructions in the FAQ:

-----------------------------------------------------------------------------------------------------------------------------------------

How can I get the "cube" effect? - overdrank

    (Image) First, install compizconfig-settings-manager. Then, in **System > Preferences > Advanced Desktop Effects Settings**, go to General Options, Desktop Size tab, and make sure Horizontal Virtual Size is set to 4. Go back to the main window, and enable the Desktop Cube and Rotate Cube plugins.
    You can "spin" the cube by pressing Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and click and drag.

----------------------------------------------------------------------------------------------------------------------------------------

OK. But there is one problem... there is NO SUCH THING as "Advanced Desktop Settings" in System>Preferences.

Do I need to install some extra package? Thanks in advance.

---

### Post by dse.37 on 2009-02-05
Fire up a terminal window and type:

```
sudo apt-get install compizconfig-settings-manager
```

After installation you should have your Advanced Desktop Settings in the above location.

---

### Post by 2hot6ft2 on 2009-02-05
It's already installed in 8.10.
Ok, right click on an empty spot somewhere on your desktop
select "Change Desktop Background" left click on it.
choose the last tab "Visual Effects"
check the dot next to "Extra"
Once it starts the effects properly choose ok and close it.

Next you can go to
Applications>Accessories>Terminal
and put in ```
ccsm
``` and hit Enter
that will open up compiz-fusion manager
Now choose your desired effects, there are a lot to choose from and the cube effect is real obvious
click on it, mark the check box on the left to enable it and make a note of the keys used to activate it.

The "Super key" is the one with the windows logo on it on your keyboard.

Enjoy.

Notes: Your graphics cards driver has to be installed AND active for them to work. You can install and activate it in
System>Administration>Hardware Drivers

If yours is a wubi install you should say so in your original post and ask in the wubi section as it's not the same as a real install which I am assuming here.

---

### Post by photon_man62 on 2009-02-05
It's a real install.

By the way, I did ALL of that much earlier, but when I press Ctrl+Alt+Down, nothing happens. I tried different key combinations. Nothing.


Any help?

---

### Post by 2hot6ft2 on 2009-02-05
> **photon_man62 said:**
> It's a real install.

By the way, I did ALL of that much earlier, but when I press Ctrl+Alt+Down, nothing happens. I tried different key combinations. Nothing.


Any help?
I believe the combo is Ctrl+Super Key+down
personally I use the mouse so I use Ctrl+Super key+left mouse button to rotate it.

---

### Post by 2hot6ft2 on 2009-02-05
Are there any desktop effects working?

---

### Post by photon_man62 on 2009-02-05
> **2hot6ft2 said:**
> Are there any desktop effects working?

Everything seems to work. Fire, water, wobbly windows...

Only the cube doesn't seem to work.

---

### Post by 2hot6ft2 on 2009-02-05
> **photon_man62 said:**
> Everything seems to work. Fire, water, wobbly windows...

Only the cube doesn't seem to work.
The only one that doesn't work is the one you want. Since everything else works check to make sure that both check boxes are marked.

There is one box in the main window of the ccsm and another when you click on the cube effect it will be on the left.

---

### Post by 2hot6ft2 on 2009-02-05
See screenshots below for the check boxes I'm talking about.

---

### Post by photon_man62 on 2009-02-05
Both are checked. :(

I guess I am screwed.

Anyways, I will check if it WORKS on my new computer a bit later.

Cheers.

---

### Post by 2hot6ft2 on 2009-02-05
That's strange. As you could see I don't have them enabled on this pc since I just use it for the web. It's probably something simple that's getting overlooked. Sorry I didn't get it going for you.

---

### Post by photon_man62 on 2009-02-05
Doesn't work on my new computer either.

All I get is the thing in the attachment (with the combination Ctrl+Alt+Down).

I changed it to Ctrl+Super+Down. Doesn't work either.

---

### Post by pbotros1234 on 2009-02-05
For the cube to work, you make sure you have 4 desktops.

Go to your CCSM > General Options > Desktop Size > Horizontal Virtual Size = 4

Not sure if this will cure my problem, but I know the cube does not work with any other than four desktops.

---

### Post by elmago79 on 2009-02-06
Also, in order for the cube to work, you need to have enabled Desktop Cube, Viewport Switcher and Rotate Cube, otherwise, your cube won't work.

---

### Post by photon_man62 on 2009-02-08
> **pbotros1234 said:**
> For the cube to work, you make sure you have 4 desktops.

Go to your CCSM > General Options > Desktop Size > Horizontal Virtual Size = 4

Not sure if this will cure my problem, but I know the cube does not work with any other than four desktops.

Yeah. That helped me. Thanks!

---

