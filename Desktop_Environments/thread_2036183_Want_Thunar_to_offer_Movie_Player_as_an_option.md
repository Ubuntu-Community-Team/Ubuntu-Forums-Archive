---
title: "Want Thunar to offer Movie Player as an option"
date: 2012-08-01
forum: Desktop Environments
---

### Post by vasa1 on 2012-08-01
In Nautilus, if I right-click on a folder that contains only .ogg files, I get the option to open the folder with Movie Player (image on the right). (I have associated .ogg files with Movie Player.)

Thunar doesn't give me that option "out of the box" (image on the left). I just get "open" and "open in a new window". Is there a way to tell Thunar to do as Nautilus does?

---

### Post by LewisTM on 2012-08-01
You can easily add that function with Thunar custom actions.
I don't know what your Movie Player is, let's use VLC as an example.

Go to Edit -> Configure custom actions...
Add a new action
Name: Open in VLC
Description: Open the folder contents in VLC and start the playlist
Command: vlc %f
Icon: You choice
Appearance conditions: Directories only

Right-clicking a folder should now show a menu item to open VLC with all contents added in the playlist. Be careful though that even nonplayable files will be added. You can work around that by refining the command:
```
vlc %f/*.ogg %f/*.mp3 %f/*.wav
```

Cheers!

---

### Post by vasa1 on 2012-08-01
Movie Player = Totem.

But what you've suggested is exactly what I want so I'm marking this as Solved.

Thank you, once again :)

---

### Post by tdlam on 2012-08-02
This did not work for me. I followed the instructions exactly and VLC does not show up in the otions.

---

### Post by vasa1 on 2012-08-02
> **tdlam said:**
> This did not work for me. I followed the instructions exactly and VLC does not show up in the otions.
Please do the following.
Open Thunar.
Click on edit and then on preferences.
Then click on custom actions. Take a screenshot of that.
Then click on the entry related to VLC. (You should have one!) Take a screenshot of that.
Notice there are two tabs.
Click on the second tab. Take a screenshot of that.
Attach all three screenshots in your next post.

---

