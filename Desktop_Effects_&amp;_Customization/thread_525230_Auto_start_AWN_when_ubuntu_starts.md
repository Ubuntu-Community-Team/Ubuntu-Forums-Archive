---
title: "Auto start AWN when ubuntu starts?"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by conradlyn on 2007-08-14
Hi there.

I have install awn and make it a little look like mac style,and more have add launchers on it,all these work well.

and i now wondering if i can make it auto start when i log in ? i  add avant-window-navigator to the sessions, but it doesn't work,and every time i log in,first thing to do is start awn.any help would be appreciated.

there is another problem with my gnome.

i use gconf-editor to make those defaultly shown harddisks on my desktop disappear,and choose something else to be shown,like my computer and trash bin.but somehow i misktakenly change one of those things,it's property should be "string" but it is now "int",anyone know how to change it back.seems can not be done in the gconf-editor because the property box is grey.and i wondering if any configuration file of this thing can be found ?

many thanks!

---

### Post by walkerk on 2007-08-14
edit: Didn't read thoroughly. You've already tried sessions.

I run a script through Sessions that loads Compiz fusion after a 7 second timeout and then another 2 seconds for AWN. 

Just an idea.

~/effects.sh
```
sleep 7 
compiz --replace &

sleep 2
avant-window navigator &
```

also, make it executable
```
chmod +x ~/effects.sh
```

Now add it to sessions.

Name: Desktop Effects
Command: ~/effect.sh


You might need to mess around with it a bit..

---

### Post by conradlyn on 2007-08-14
thanks for your reply, mate.

but, i am wondering if i can use "fusion-icon" instead of  "compiz--replace"? cuz i am afraid of this replace might just take my window frame away when restarted. 

also, i have another problem with emerald theme manager.  i have managed the theme (shadow,border,buttons etc.) to be perfect for me with  emerald. and when the machine was restarted, all these managements disappear, instead, the theme changed back to metacity (or gtk ) one,this is making crazy. and now whenever i log in, i have another thing to do : make the theme accetable for me again. How it can be solved please ?

---

### Post by FuturePilot on 2007-08-14
System>Preferences>Sessions
Click New. Add a Title for it then for the command enter
```
avant-window-navigator
```

---

### Post by walkerk on 2007-08-14
> **conradlyn said:**
> thanks for your reply, mate.

but, i am wondering if i can use "fusion-icon" instead of  "compiz--replace"? cuz i am afraid of this replace might just take my window frame away when restarted. 

also, i have another problem with emerald theme manager.  i have managed the theme (shadow,border,buttons etc.) to be perfect for me with  emerald. and when the machine was restarted, all these managements disappear, instead, the theme changed back to metacity (or gtk ) one,this is making crazy. and now whenever i log in, i have another thing to do : make the theme accetable for me again. How it can be solved please ?

you have to start compiz + emerald at every boot. metacity is the default window manager and will load with each login. This is why you need to load compiz (i guess you use the fusion icon.. but its not necessay). 

depending on which build of compiz fusion you can load it by pressing aflt-f2 (or terminal) and entering```
compiz --replace -c emerald &
```

or if that doesn't work you need to use this```
compiz --replace && sleep 2 && emerald --replace &
```

---

### Post by conradlyn on 2007-08-15
> **FuturePilot said:**
> System>Preferences>Sessions
Click New. Add a Title for it then for the command enter
```
avant-window-navigator
```

i have tried this out after the awn was installed, but it didn't work,so i am here asking for help.

> **walkerk said:**
> you have to start compiz + emerald at every boot. metacity is the default window manager and will load with each login. This is why you need to load compiz (i guess you use the fusion icon.. but its not necessay). 

depending on which build of compiz fusion you can load it by pressing aflt-f2 (or terminal) and entering```
compiz --replace -c emerald &
```

or if that doesn't work you need to use this```
compiz --replace && sleep 2 && emerald --replace &
```

yeah,your are right,i am using fusion-icon.the "compiz--replace -c emereald &" code do load compiz in my last try,but this would take my window borders away,then with fusion-icon,it's ok.so i chose icon.the thing is,compiz and emerald did start when login,but emerald did not load a theme.

and maybe i will try your second code later...

anyway, thanks for your help.:)

---

### Post by frozenjim on 2008-05-07
> **conradlyn said:**
> i have tried this out after the awn was installed, but it didn't work,so i am here asking for help.

I add my confirmation.  After upgrading to Hardy (or that's when I started to notice it anyhow) my Sessions information seems to be ignored.

I deleted Cairo Clock and gDesklets from my session list but they still show up at every start.  I added avant-window-navigator to the session but it doesn't start.

Is the Session Manager being ignored now?

---

