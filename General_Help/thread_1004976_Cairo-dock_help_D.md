---
title: "Cairo-dock help D:"
date: 2008-12-07
forum: General Help
---

### Post by jorgecarrillo150990 on 2008-12-07
I have been using cairo-dock for a while now, but I can't cuztomize it as much as I like since it is in French.
Well, the point of this thread is to ask how to make a launched application appear in the same icon as the launcher (if you have used AWN you know what I am talking about).
Right now when I open an application it appears in another area of the dock with an ugly icon :P
so, any suggestions?

---

### Post by kawaji on 2008-12-08
"Overwrite X icons with launchers' one ?" option is enabled ?
If it did not work for the application you mentioned, try the following steps.

1. Open terminal window and the application window.

2. Run the following command from the terminal.
```
xprop|grep WM_CLASS|cut -d\" -f4
```

3. A mouse pointer will be changed to a cross-hair, Put the cross-hair pointer on the application window, and Click on it.

4. A class name of the window will be outputted on the terminal.

6. Select "Modify this launcher" from cairo-dock context menu.

7. Click "Extra Parameters".

8. Copy & Paste the class name into the entry box of "Class of the program".

---

### Post by Ng Oon-Ee on 2008-12-08
> **kawaji said:**
> "Overwrite X icons with launchers' one ?" option is enabled ?
If it did not work for the application you mentioned, try the following steps.

1. Open terminal window and the application window.

2. Run the following command from the terminal.
```
xprop|grep WM_CLASS|cut -d\" -f4
```

3. A mouse pointer will be changed to a cross-hair, Put the cross-hair pointer on the application window, and Click on it.

4. A class name of the window will be outputted on the terminal.

6. Select "Modify this launcher" from cairo-dock context menu.

7. Click "Extra Parameters".

8. Copy & Paste the class name into the entry box of "Class of the program".
Thanks for that very useful post, just ran across it, now I know a very useful command for finding the class name of a window, and also the fact that Cairo groups according to class name. Brilliant.

To the OP, my Cairo-dock is totally in English, why is yours in French?

---

