---
title: "Gnome shell dash has duplicate icons: My solution."
date: 2018-07-01
forum: Desktop Environments
---

### Post by 0c-bill on 2018-07-01
[SIZE=4][FONT=times new roman]I like Vanilla Gnome 3 best, but I also really wanted to use Amarok, a KDE music player. But, I discovered that whenever I ran Amarok it would place a second icon in the Gnome Shell Dash.

I scoured the web looking for a solution. I found a few and tried each. No luck. The most promising was the technique of adding a line with "[/FONT][COLOR=#111111][FONT=times new roman]StartupWMClass="[classname] to the relevant .desktop file. This *looks* easy, but it proved to be a fruitless endeavor. Despite my efforts to find and add this line to a .desktop file, it was as if I could not find the correct .desktop file.

Then I had an inspiration - what if I let the Dash fix itself? Here is what I did:[/FONT]
[FONT=arial]1. Run the application using the icon from the dash. In my case this was Amarok. This technique *might* work without having it already on the Dash, but I haven't tried that yet.
2. Once the extra icon appears one of them will have the "running" indication. In my case this is a thin little line under the icon. Also in my case, this was the new icon which showed up with the running indication.
3. In the Dash, locate the icon that does **not** have the running indiciation. Right-click this icon and select the option which removes it from Favorites.
4. Notice there is now only one icon for the application in question-the icon that has the "running" indication under it.
5. In the Dash, right-click the remaining icon and select to add it to Favorites.
6. Completely close/exit the application in question.
7. In the Dash, notice that there is still an icon for the application and that it does **not** have a "running" indication.
8. From the Dash, run the application. After it starts up, notice that there is still only one icon, and that it has a "running" indication.[/FONT]

[FONT=times new roman]Of course, I will have to wait and see if this persists through a few restarts, but I am optomistic.

If anyone can suggest a better place for this post, please let me know.[/FONT][/COLOR][/SIZE]

---

### Post by vanadium on 2018-07-01
Good place of this post if you ask me ;) but especially thanks for sharing this experience: this may help other users in solving occasional little quirks with the icons in the dash. I also feel this will continue to work right, but advise us if it would not.

---

### Post by 0c-bill on 2018-07-01
[SIZE=3]The fix didn't last. It has gone back to showing two icons in the Dash when Amarok is running. Strangely, the extra icon has a different image/style. Also, now, I cannot apply the fix I used previously. The new icon will not offer up an option to add it to the favorites when right-clicked.

I will continue to investigate this as I am able. I am sure this has to do with the differences between KDE and the Gnome desktop that I am using it on...[/SIZE]

---

