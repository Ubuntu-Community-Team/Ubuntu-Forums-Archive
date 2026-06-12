---
title: "Problem with starting gtk-using programs"
date: 2009-12-04
forum: Desktop Environments
---

### Post by Mentosfresser on 2009-12-04
Hi everyone,
In Google there were nothing that solve this, so i ask here.
as the topic says, i have a problem with starting some programs. For example pidgin, synaptic, inkscape and gimp. The first three give the follow Errormessage in a shell:
```
symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle
```

with gimp i get this:
```
gimp: symbol lookup error: gimp: undefined symbol: pango_version_check
```
 I am using Kubuntu 9.04. It worked before, but i tryed to compile and install gtk and pango (at gtk i failed with make, but pango was successfull installed). I think thats the problem. 


Thanks for help :)
Pascal

---

### Post by Tomatz on 2009-12-04
> **Mentosfresser said:**
> Hi everyone,
In Google there were nothing that solve this, so i ask here.
as the topic says, i have a problem with starting some programs. For example pidgin, synaptic, inkscape and gimp. The first three give the follow Errormessage in a shell:
```
symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle
```

with gimp i get this:
```
gimp: symbol lookup error: gimp: undefined symbol: pango_version_check
```
 I am using Kubuntu 9.04. It worked before, but i tryed to compile and install gtk and pango (at gtk i failed with make, but pango was successfull installed). I think thats the problem. 


Thanks for help :)
Pascal

> Correct! I suddenly had a failing xsane plugin in gimp. Running xsane at the terminal gave me the same symbol error described in this forum. Deleting an older version of libgobject (libgobject-2.0*) in /usr/local/lib and keeping the newer one in /usr/lib fixed this problem!
 
 Correct! I suddenly had a failing xsane plugin in gimp. Running xsane at the terminal gave me the same symbol error described in this forum. **Deleting an older version of _[SIZE="2"]libgobject (libgobject-2.0*)[/SIZE]_ in _[SIZE="2"]/usr/local/lib[/SIZE]_ and keeping the newer one in /usr/lib fixed this problem!**
 
Definitely wanted to post this feedback as googling even part of: 
 
 "xsane: relocation error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_object_compat_control"
 
 ..brought up only FOUR pages, this one being one of them. Thanks!

From:

[http://www.linuxquestions.org/questions/slackware-14/symbol-lookup-error-usrliblibgtk-x11.2.0.so.0-undefined-symbol...-434399/](http://www.linuxquestions.org/questions/slackware-14/symbol-lookup-error-usrliblibgtk-x11.2.0.so.0-undefined-symbol...-434399/)

Hope it helps :)

---

### Post by Mentosfresser on 2009-12-05
Weeheew thx Tomatz,
after deleting one library, getting a new error, deleting another library, getting another new eror, deleting another library it finally worked ^.^ 
Thx for fast reply, the next time i only use parts of the errormessage on google Oo

MfG Pascal

oh and thx again ^^

---

