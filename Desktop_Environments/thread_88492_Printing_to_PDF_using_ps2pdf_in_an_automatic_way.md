---
title: "Printing to PDF using ps2pdf in an automatic way"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Hellaxe on 2005-11-10
Hi people:
what i wan't is to print to a "virtual printer", or if you prefer, to a *.pdf file any document in any software or firefox for exemple. I can do that using ps2pdf to convert the *.ps files but i want to do it in an automatic way like this:

Print to file -> *.pdf. 

Is it possible? i think kde do this.

I know OOffice has this feature. But what about other programs?

---

### Post by Hellaxe on 2005-11-16
Hello People any ideas:confused:

---

### Post by ow50 on 2005-11-16
[QUOTE=Hellaxe]Hi people:
what i wan't is to print to a "virtual printer", or if you prefer, to a *.pdf file any document in any software or firefox for exemple.[/QUOTE]
PDF-printing support seems to be in Gnome apps that use the standard Gnome print dialog.

Here's a rough list of those apps (packages actually):
```
$ apt-cache rdepends libgnomeprint2.2-0 | grep -v lib | grep "  " | sort
  abiword
  abiword-gnome
  anjuta
  balsa
  conglomerate
  drivel
  eog
  epiphany-browser
  epiphany-browser
  evince
  evince
  evolution
  evolution-exchange
  evolution-plugins
  gchemutils
  gedit
  ghex
  glabels
  gnome-photo-printer
  gnomesword
  gnometab
  gnome-utils
  gnome-u2ps
  gnotime
  gnumeric
  goats
  gobby
  gpaint
  gpdf
  gthumb
  gthumb
  gtkhtml3.6
  gtkhtml3.8
  mergeant
  mozilla-bonobo
  mysql-query-browser
  oregano
  peacock
  planner
  python2.4-gnome2-extras
  screem
  screem
  sylpheed-claws-gtk2
  xlog

```

---

### Post by Hellaxe on 2005-11-16
Thanks ow50.

But when i need to print something from Firefox i can´t get it.
What i was trying is enabling that feature for all apps that i use.
Was my explanation clear?

---

### Post by metasyntax on 2005-11-16
This is actually quite easy:

the package you are looking for is "cups-pdf", install it using synaptic.  Then goto System->Administration->Printing, you should see "PDF Printer" as a "detected printer", select it, and click "forward".  From the "Manufacturer" dropdown, select "Generic", with the model as "postscript color printer (rev3)".  Click "Apply".

Now you have edit /etc/cups/cupsd.conf, and change the line:
```

RunAsUser Yes

```
to
```

RunAsUser No

```

finally, restart cupsd
```

sudo /etc/init.d/cupsd restart

```

You should now be able to print from any Linux application to a PDF file that is created in your $HOME directory.

hth,
meta

---

### Post by rider343 on 2005-11-17
Works fine, thank you :)

---

### Post by Hellaxe on 2005-11-17
OK Thank you very much.
You saved my day:-D

Edit: You should do

> sudo /etc/init.d/cupsys restart

because there is no cupsd in init.d, at least in my system.

---

### Post by dro0g on 2005-11-22
[QUOTE=metasyntax]This is actually quite easy:

meta[/QUOTE]

That worked great, thanks for the fantastic instructions!

---

### Post by shadow07 on 2005-11-22
[QUOTE=metasyntax]This is actually quite easy:

the package you are looking for is "cups-pdf", install it using synaptic.  Then goto System->Administration->Printing, you should see "PDF Printer" as a "detected printer", select it, and click "forward".  From the "Manufacturer" dropdown, select "Generic", with the model as "postscript color printer (rev3)".  Click "Apply".

Now you have edit /etc/cups/cupsd.conf, and change the line:
```

RunAsUser Yes

```
to
```

RunAsUser No

```

finally, restart cupsd
```

sudo /etc/init.d/cupsd restart

```

You should now be able to print from any Linux application to a PDF file that is created in your $HOME directory.

hth,
meta[/QUOTE]

Why do you need to change the RunAsUser Yes to No?  From what I read, this is not recommended.

---

