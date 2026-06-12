---
title: "Unhide Menu Bar"
date: 2009-04-28
forum: General Help
---

### Post by kraines on 2009-04-28
By accident I hid my menu bar, the one with file, edit, view, ect.  the Ubuntu guide says to hit view to enable menu bar, so how do i hit view if it is hidden??  I have tried Alt+V, but it  does not bring up the view menu

---

### Post by click170 on 2009-05-05
I just ran into this problem myself, and upon Googling, came upon your blog post.  
For me, I had hidden the menubar in a terminal window.  After looking around the solution seems to be, at least for me using terminal, to right click on the terminal window and select 'Show Menubar'.
Hope this is helpful to other people too :)

---

### Post by TheOmegaCrisis on 2011-07-01
I did this too! I actually hid all bars, so i couldnt unhide by right-clicking on any other bar 
press alt+F2 - type in "gconf-editor" and click run
goto apps>nautilus>preferences
go to the bottom of the list, you'll find :
start_with_menubar
start_with_sidebar
start_with_status_bar
start_with_toolbar

check whatever u want and u r done!!

---

