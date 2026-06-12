---
title: "Assign water effect on doubleclick (Gutsy)"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by ubanto on 2008-02-19
First of all Compiz works properly and has shows noone of the recurring problems on my system.
By the way, I want to configure the water effect on double click, to impress my non tech-savy friends.
I go to
System>Preferences>Advanced Desktop Settings
I open the Water Effect panel, and select the 'Action' tab.
On the 'Start' action, default is <Control><Super> but when I try to change that it only accepts keyboard values (like <Control><Super>+any character), and it is not possible to change it to a mouse gesture (in this case a simple doubleclick), or even go back to the default value.
Is it normal in an otherwise fully working configuration?
Any hint on how to solve that?
Thanks everybody.

---

### Post by jesusfreak180 on 2008-02-19
This would be awsome! anyone know how?

---

### Post by ubanto on 2008-02-20
Yes and imagine when the double click becomes a double tap on a tablet...
How many people I could be able to convert...
I hope some compiz guru can help...

---

### Post by ubanto on 2008-02-20
OK, I am trying to figure it out by myself, however I still need help.
I do sudo nautilus (yes I'm a lazy basterd), and i go to
/home/[username]/.gconf/apps/compiz/plugins/water/allscreens/options/
where the %gconf.xml file with the shortcuts is stored.
I doubleclick that (you probably prefer to sudo gedit that from terminal) and I see the line that I'm interested in:

<entry name="initiate_key" mtime="1203507676" type="string">
                <stringvalue>[theuselesskeyboardshortcut]</stringvalue>

Now I shift the question: does anybody knows what's the proper Compiz readable expression for 'doubleclick'? Even a single click would be a start. I tried Button1 but it doesn't work, and I can't figure it out even after reading all the other plugins %gconf files...

---

### Post by DaymItzJack on 2008-02-20
From looking at my compiz. you can't start it with a button, it has to be a key.

---

