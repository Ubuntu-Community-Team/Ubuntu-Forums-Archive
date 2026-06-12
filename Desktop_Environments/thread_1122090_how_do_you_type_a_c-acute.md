---
title: "how do you type a c-acute?"
date: 2009-04-10
forum: Desktop Environments
---

### Post by ireneshusband on 2009-04-10
I sometimes need to type a c-acute. [https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable) says that compose c apostrophe and compose apostrophe c should do it, but they give me a c-cedilla. I have also tried using dead-acute c on the us international altgr dead keys layout, but that also gives my c-cedilla. How do I get a c-acute?

---

### Post by maheshasolkar on 2009-04-10
I use the USA keyboard layout. Under Keyboard preferences (System -> Preferences -> Keyboard), on the 'Layouts' tab, there is an 'Other Options...' button. There, you can set the 'Compose Key Position'. I've set it to 'Right Ctrl is Compose'.

Now typing "Compose (Right Ctrl) + single-quote (')" followed by c, I get &#263;. Similarly, "Compose (Right Ctrl) + single-quote (')" followed by a/e gives á, é etc.

Hope this helps.

---

### Post by ireneshusband on 2009-04-10
> **maheshasolkar said:**
> I use the USA keyboard layout. Under Keyboard preferences (System -> Preferences -> Keyboard), on the 'Layouts' tab, there is an 'Other Options...' button. There, you can set the 'Compose Key Position'. I've set it to 'Right Ctrl is Compose'.

Now typing "Compose (Right Ctrl) + single-quote (')" followed by c, I get &#263;. Similarly, "Compose (Right Ctrl) + single-quote (')" followed by a/e gives á, é etc.

Hope this helps.

Thanks for your reply.

Unfortunately this is not the behaviour I get in GTK applications. For instance, as I have said, compose apostrophe c yields ç. This is not the case in KDE applications, for instance I am able to copy and paste &#263; here after entering it using a the same compose key combination in Amarok. I can also do the same thing using the dead acute on my keyboard layout. Can I just check that you are using a GTK application for this, such as gedit?"

---

### Post by VCoolio on 2009-04-10
Depending on the frequency of 'sometimes' you may want to change your input method to XIM. search this forum or the web on howto's. If 'sometimes' really is sometimes then please don't mess around and import it from the character map or set in openoffice for example c/ to be autoreplaced by &#263;.

---

### Post by adamitj on 2009-04-10
Well... character map is basically defined by the keyboard layout you selected when installing + the default OS language.

For me, I speak brazillian portuguese. However, to maintain compatibility with some softwares I use an english-UK language in my Ubuntu. 

My notebook keyboard is United States International (us_intl), so even if I select portuguese language at the installation (or set it after) I can't get the cedilla character "ç" when typing apostrophe + c ('+c). In replace of it, I get a c-accute "&#263;", a character that does not exists in portuguese.

So I need to change my file ```
/usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules
``` and check for ```
“cedilla” “Cedilla” “gtk20&#8243; “/usr/share/locale” “en:az:ca:co:fr:gv:oc:pt:sq:tr:wa”
```

Where I put the "en:" and then cedilla works fine.

[SIZE="4"][COLOR="SeaGreen"]**I don't know what is your default language, so try to remove its code from "cedilla section" of immodule-files.d and restart your X.**[/COLOR][/SIZE]

---

### Post by ireneshusband on 2009-04-11
Thanks for that. I did in fact change my default language to French recently. When I log in as an English-using user I don't get this issue.

I still can't see the point of mapping ç onto dead acute c and compose 'c. All the layouts for French-speaking countries and regions already have a ç at first or second level.

---

### Post by adamitj on 2009-04-12
If my last option does not worked, check out the file```
/usr/share/X11/locale/en_US.UTF-8/Compose
```and search for all entries of "ç" & "Ç" and change them to "&#263;" and "&#262;".

Remember that this is not a per user set. It will affect all users of your OS. And, please make a backup of the files before change them.

---

