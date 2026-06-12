---
title: "reset to default value"
date: 2009-05-17
forum: General Help
---

### Post by soulasylum on 2009-05-17
I set up value of computer_name by gconf-editor.I changed -->app-->nautilus-->desktop-->computer_icon_name from *no value* to 0.After that every time When I start my computer it will appeared this message.
[I]An error occured while loading or saving configurarion information for gnome-panel.some of your configuration settings may not work properly.
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name[/I]
Anyone can help to fix this problem?

---

### Post by mb_webguy on 2009-05-17
The computer_icon_name field has to be a string, not an integer, which is why you're getting the error.

If you can't login the normal way, login using the recovery console from the GRUB menu.  Then enter the command "nano /home/*username*/.gconf/apps/nautilus/desktop/%gconf.xml", and look for the bit that looks something like this:```
	<entry name="computer_icon_name" mtime="1240547036" type="string">
		<integervalue>0</integervalue>
	</entry>

```
Change that to look like the following:```
	<entry name="computer_icon_name" mtime="1240547036" type="string">
		<stringvalue>*whatever you want to call your computer*</stringvalue>
	</entry>

```
Save, exit, and reboot (using the "reboot" command).  Now you should be able to login normally.

---

### Post by soulasylum on 2009-05-18
Thank U guy.My problem was fix by doing on your suggestions.

---

