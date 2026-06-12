---
title: "Desktop Icons"
date: 2009-06-14
forum: General Help
---

### Post by nlmaster on 2009-06-14
Ubuntu Linux 9.04.   

Would like to add some icons to my desktop for ease of use. Have figured out how to add the Computer icon by Alt+F2; gconf-editor; >apps>nautilus>desktop but would also like to add the documents folder to the desktop and can't figure out how. 
Any suggestions.

Nlmaster

---

### Post by ibuclaw on 2009-06-14
The most generic way would be to open Nautilus, right-click on "Documents" and select "**Make link**".

Then move the "**Link to Documents**" to your Desktop, and rename it.

Regards
Iain

---

### Post by TrakerJon on 2009-06-14
Get your Trash Can and other desktop icons back...

The default for new installed Ubuntu is clean desktop. So, for example, if you want to get your Trash Icon back you need to change the default setting.

Step 1. Run Desktop Configuration Editor

Open Application > Accessories > Terminal and type gconf-editor.

Step 2. Change the value for trash_icon_visible

After the Desktop configuration Editor is displayed, open apps > nautilus > desktop and click the value for trash_icon_visible. This also works for your computer, home and network icons.

---

### Post by cmost on 2009-06-14
Another very easy way to add custom icons for various items such as folders or applications is the following:

For folders:
1.  Right-click desktop and select "create launcher"
2.  Fill out the resulting dialog as follows:
    Name = Name of folder (i.e., "My Music")
    Command = nautilus /path/to/music (your own specific path obviously)
    Comment = My music collection (or whatever you like)

For Applications:
1.  Right-click desktop and select "create launcher"
2.  Fill out the resulting dialog as follows:
    Name = Name of Applications (i.e., "Firefox"
    Command = firefox %u (use the name of any executable, even scripts if you like, just specify the path to the script)
    Comment = Browse the World Wide Web (or whatever you like)

Good luck!

---

### Post by nlmaster on 2009-06-14
> **TrakerJon said:**
> Get your Trash Can and other desktop icons back...

The default for new installed Ubuntu is clean desktop. So, for example, if you want to get your Trash Icon back you need to change the default setting.

Step 1. Run Desktop Configuration Editor

Open Application > Accessories > Terminal and type gconf-editor.

Step 2. Change the value for trash_icon_visible

After the Desktop configuration Editor is displayed, open apps > nautilus > desktop and click the value for trash_icon_visible. This also works for your computer, home and network icons.

Thanks. I have the Trash Can on the desktop now.

---

### Post by nlmaster on 2009-06-14
> **tinivole said:**
> The most generic way would be to open Nautilus, right-click on "Documents" and select "**Make link**".

Then move the "**Link to Documents**" to your Desktop, and rename it.

Regards
Iain

Ok. I got it but I accidently deleted the Documents Folder. Can I get it back? If so how?

---

### Post by cmost on 2009-06-15
> **nlmaster said:**
> Ok. I got it but I accidently deleted the Documents Folder. Can I get it back? If so how?

Create a new launcher with command "nautilus /home/username" (where username is YOUR username)

Alternately, go to gconf-editor-->apps-->nautilus-->desktop and tick the checkbox for "home icon visible"

---

### Post by nlmaster on 2009-06-15
> **cmost said:**
> Create a new launcher with command "nautilus /home/username" (where username is YOUR username)

Alternately, go to gconf-editor-->apps-->nautilus-->desktop and tick the checkbox for "home icon visible"

Thanks CMost. You were a big help. Much appreciated.

nlmaster

---

