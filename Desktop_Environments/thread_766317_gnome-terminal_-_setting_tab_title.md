---
title: "gnome-terminal - setting tab title"
date: 2008-04-25
forum: Desktop Environments
---

### Post by mygravity on 2008-04-25
Hi,

When working I like to have two terminals open:

1) with two tabs with titles set to DEV, BUILD
2) with two tabs with titles set to CLIENT, SERVER

I want to create a launcher/shell script to open these terminals with one click. Is that possible?

So far I've managed to open a terminal with two tabs using:
```
gnome-terminal --tab-with-profile=Default --tab-with-profile=Default
```

However I'm not sure how to set the title of individual tabs.

Does anyone know?

Many thanks

Andrew

My system:
GNOME 2.16.1
Ubuntu 6.10 Edgy Eft

---

### Post by pertti on 2008-04-25
You could create a profile for each kind of tab. Go to Edit > Profiles > New. Give it a name, which you will use in the command line (e.g. DEV-terminal). In the next tab set the title to the one you want, and select not to show the dynamic title.

Then call gnome-terminal with the new profles:

```
gnome-terminal --tab-with-profile=DEV-profile --tab-with-profile=BUILD-profile
```

Hope this works

---

### Post by steve8track on 2011-05-25
I just found out a better way:

Create a profile that keeps the original title, then set it in the command line:

```

gnome-terminal --tab-with-profile=Titleable -t "Title HERE"
```

That way you don't need a different title per tab/terminal.  You can string them together like this:

```

gnome-terminal \
	--tab-with-profile=Default \
	--tab-with-profile=Titleable -t "Title" \
	--tab-with-profile=Titleable -t "Apache Error Log" -e "tail -f /var/log/apache2/error.log"

```

---

