---
title: "How can i set tree view only in nautilus (16.04)"
date: 2016-05-18
forum: Desktop Environments
---

### Post by lucas60 on 2016-05-18
Hello everyone :),

So right now I have the tree view enabled but its really a pain to always click that little drop-down button next to the folder. So I was wondering if I could make it so that all folders will be opened in a tree view regardless of where I click. Already thanks in advance. :)

Sincerely yours,
Lucas

---

### Post by QDR06VV9 on 2016-05-18
Yes that option has been removed but a quick install of** "dconf-editor**"
Should get you the desired view.
I installed dconf-editor  in the tool I found the section <org>.<gnome>.<nautilus.list-view>, and here a check-box option use-tree-view. This allowed me to display a tree in the right pane. An acceptable work-around. I hope there is a better way, not requiring dconf-editor, directly from Nautilus.(Gnome Devs)
Edit: forgot to mention you need to log out and back in again for the change to stick.
kind regards

---

### Post by lucas60 on 2016-05-18
Thank you very much its way better now. Also thanks for replying so quick :)

---

### Post by QDR06VV9 on 2016-05-18
> **lucas60 said:**
> Thank you very much its way better now. Also thanks for replying so quick :)

Nice Glad it worked!
I will mark this as solved as to help others.
Happy Ubuntu-ing!
Kind regards

---

### Post by mc4man on 2016-05-18
> **runrickus said:**
> I hope there is a better way, not requiring dconf-editor, directly from Nautilus.(Gnome Devs)

Still here in nautilus -  Edit > Preferences > Display > List View

---

### Post by SuperFreak on 2016-05-18
menu options have disappeared since I upgraded to 16.04(such as Edit) in my Nautilus which may be OPs situation also

---

### Post by mc4man on 2016-05-19
> **SuperFreak said:**
> menu options have disappeared since I upgraded to 16.04(such as Edit) in my Nautilus which may be OPs situation also
If you don't have [menu items in an ubuntu session]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226") then log out/in or run this command
```
initctl restart unity-panel-service
```
In a gnome session it's Files dropdown > Preferences > ....

---

### Post by QDR06VV9 on 2016-05-19
> **mc4man said:**
> Still here in nautilus -  Edit > Preferences > Display > List View
That is just weird...but I am using Ubuntu Gnome Shell 3.20 and do not see that option.
I see all of what you show in your screen shot but No Tree View box to check off.

---

### Post by mc4man on 2016-05-19
> **runrickus said:**
> That is just weird...but I am using Ubuntu Gnome Shell 3.20 and do not see that option.
I see all of what you show in your screen shot but No Tree View box to check off.
Probably not weird, maybe Gnome has removed option from gui. Atm 3.20 is far removed from what Ubuntu/Ubuntu-Gnome  are using.

---

### Post by QDR06VV9 on 2016-05-19
Yes that makes sense now.
I tend to forget that I use newer software that others may not feel comfortable with yet.
I will say Gnome 3.20 **Dose Not** play nice with Unity ATM.
Thanks for the memory jog mc4man

---

### Post by izznogooood on 2016-05-20
There is kind of a mutiny option available here: I use nemo. (I dont replace nautilus completely though)

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

[ATTACH=CONFIG]269186[/ATTACH]

---

