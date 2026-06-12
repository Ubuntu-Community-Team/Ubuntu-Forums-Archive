---
title: "Super key mapped to 'full screen' - can't unmap"
date: 2008-10-25
forum: Desktop Environments
---

### Post by mageus on 2008-10-25
- Ubuntu 8.04, Dell Mini-9

When I press the 'Super' key it full-screens the current window.  Super isn't mapped to anything in metacity or compiz.  Does anyone know of any other place for key bindings than the 'Keyboard Shortcuts' or Compiz Setting Manager apps?


Some points:

- Keyboard Shortcuts->"Toggle fullscreen mode" = 'disabled'

- CompizConfig Settings Manager->General Options->Toggle Fullscreen = 'disabled'

- CompizConfig Settings Manager->Advanced Search->'super' - nothing is mapped to super by itself

- Keyboard Shortcuts - nothing is mapped to super by itself

- Keyboard Preferences->Layout Options->Alt/Win key behavior - tried 'Default', 'Super is mapped ot Win', etc.

- I know the Win key on the computer is mapped correctly, because when I map 'control' to 'win-key' in layout options, it works correctly.

- Tried changing keyboard layout to 104-key.

- gconf-editor - nothing is mapped to 'super' by itself


Basically, something (other than metacity/compiz) has taken over the key binding for the super key and assigned it to full-screen, but I can't figure out what.

---

### Post by mageus on 2008-10-25
In keyboard layout options I chose 'alt is mapped to the right Win-key and Super to menu'.  But pressing Menu-key does nothing.  Win-key still fullscreens windows.

In Compiz Settings->General->Key Bindings, I edit Show Main Menu.  Pressing Menu-key or Win-key both register correctly as super.  I bind 'Super' to Show Main Menu.

However, now Menu-key (mapped to Super) doesn't show the main menu.  It doesn't do anything.  Win-key still fullscreens a window, but doesn't open the main menu.

Now, I bind Super-t to Show Main Menu. Pressing Menukey-t opens up the Main Menu.  Pressing Win-key still only fullscreens a window.


Obviously, something other than compiz/metacity is grabbing my Windows key and I can't figure out what!

---

