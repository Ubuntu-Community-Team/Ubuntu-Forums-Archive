---
title: "Cant change main menu logo!"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by bvdf on 2008-03-31
hey everyone,

i want to change my menu icon and tried everything that is on the forum but i cant make it work :(

im using gnome 2.22 with ubuntu hardy 8.04

please help me 

i dont realy like the ubuntu logo that mutch

thanks

---

### Post by Amarsingh0793 on 2008-04-04
First make sure the Main Menu is on the Panel (BY clicking add to panel), then:

1. Press and Hold Alt + F2 and type gconf-editor
2. Go to apps > panel > objects
3. One of these objects shoudl be your Main Menu. If you have more than 1 object, look in the object_type field for the object that says "menu-object"
4. Tick the checkbox in the field use_custom_icon.
5. Finally, in the field custom-icon, enter the location of the Custom Logo you would like to use.

Enjoy!:)

---

