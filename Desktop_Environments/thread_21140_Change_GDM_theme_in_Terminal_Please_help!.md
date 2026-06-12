---
title: "Change GDM theme in Terminal? Please help!"
date: 2005-03-20
forum: Desktop Environments
---

### Post by andbert on 2005-03-20
Im hoary, using KDE. Gnome is also installed, but i never use it.
I recently changed the Splas/GDM to something I downloaded from kde-looks.org...

The problem started next time i rebooted.

"The theme for the graphical greeter is corrupt.
The theme does not contain definition for the username/password entry element"

And then;

"There was an error loading the theme, and the default theme also could not have been loaded, I will attempt to start the standard greeter"

Then som kind of standard human-greeter shows up.
But the area for username/password entries is "greyed" out.

So in order to fix this I'll guess I somehow have to change the splash/gdm?
But is that possible in terminal (which is the only working app remaining)
Anyone with a similar problem, or input on how to solve this?

---

### Post by andbert on 2005-03-20
Problem solved!

editing /etc/gdm/gdm.conf did it.

and deleting the corrupted theme from:
/usr/share/gdm/themes

---

### Post by rippon on 2005-10-25
Wow, same thing happened to me. I am going to try this!
The theme wasnt by chance this one, was it?
[http://kde-look.org/content/show.php?content=29226](http://kde-look.org/content/show.php?content=29226)

That is the one that did it for me :???:

Hope it workes.

---

### Post by rippon on 2005-10-25
I think the problem is that we dont have KDM installed? So we are putting a KDM in the GDM, if that makes sense. The KDM installed fixes it? Or am I completly off.

Thanks for posting how you fixed it! Helped me tons!

---

### Post by mochiko on 2008-06-05
i'm quite frustrated with this problem that i'm facing - although i click the +Add Item button and the login theme is shown in the list AND i select the theme that i want, it doesn't actually change.

It kept showing this theme (like the ubuntu beige theme). i forgot the name because i removed the item, making it permanently lost. i thought this would solve the problem. but then when i logged out and came back, a window came up and said, "the ubuntu (whatever the name is) theme cannot be found" and it showed a completely different theme than i had selected still!

i really don't know what to do. i don't believe it's for a specific theme, but it doesn't switch to any theme. if anyone has any idea on how to deal with this, i would greatly appreciate the help.


mochiko is online now Report Post   	Edit/Delete Message

---

