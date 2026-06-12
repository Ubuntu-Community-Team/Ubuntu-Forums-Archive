---
title: "Hotkey menu stuck on oblivion!"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by Copperteeth on 2007-06-27
Hey, i got TES 4 oblivion running flawlessly under wine, absolutely no graphical problems from what i can tell. So, when i go to play the game, i have a little, no, a large annoying problem! When i load my file or start a new one, it loads and the hotkey menu is stuck up with the 1 key highlited red as if im pressing it! Now this causes problems because when i go to equip an item it automaticly assigns it to the 1 key as if im pressing it all the time. if i press other number keys, nothing happens, 1 still stays highlited. I dont know how to fix this. I deleted the section in my oblivion.ini about key bindings and it still does it. I have no idea if its my version of wine or not. I used 0.9.29 and it gave me less performance than the current 0.9.39. Help me someone!

EDIT: I guess im not the only one having this problem, according to the Wine Application DB, someone else is having the same problem:
> ...because of random freezing. **The hotkey panel is always shown for some reason. **The performance isn't...

Full page can be found[** HERE**]("http://appdb.winehq.org/appview.php?iVersionId=7506&iTestingId=10972")

---

### Post by Negatratoron on 2007-11-24
You can get the hotkey menu to disappear by unplugging joysticks or gamepads and restarting Oblivion.

[http://www.uesp.net/wiki/Oblivion:Linux#The_hotkey_menu_will_not_disappear](http://www.uesp.net/wiki/Oblivion:Linux#The_hotkey_menu_will_not_disappear)

---

### Post by holr on 2008-05-07
sorry to revive an old thread, but i had the same problem with my macbook, but i didnt have a usb joypad in. In my case, the applesmc driver was making the internal motion sensor act like a joystick. All i had to do was temporarily remove the applesmc module (via a sudo modprobe -r applesmc) while the game loaded (I then loaded it again in another window while the game was running with a sudo modprobe applesmc) and voila! no more hotkey window! :-)

---

