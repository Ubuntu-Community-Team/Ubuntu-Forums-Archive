---
title: "Compiz Problems"
date: 2009-11-20
forum: Desktop Environments
---

### Post by The Real Dave on 2009-11-20
Well, was experimenting with Compiz, and turned on Reflections. My graphics card didn't like that at all, and locked up. Logging in restarts the reflections module and locks up again. 

So my question is, how can I turn off the reflections module from outside my account? I have access to /home through KUbuntu on another partition, so I can edit files if need be :)

Thanks in advance to any help, I can't see a way out other than re-installing, so I hope that someone here can show me a way :)

---

### Post by jessiebrownjr on 2009-11-20
maybe boot into recovery mode, and do a purge of the program?

---

### Post by yossell on 2009-11-21
I'm not sure if this will work but...

go to  /home/~/.gconf/desktop/gnome/session/required_components

(~ will be the name of your own home folder)

and try opening the file %gconf.xml there in a text editor. 

Hopefully, you see something like this:
<?xml version="1.0"?>
<gconf>
    <entry name="windowmanager" mtime="1258797724" type="string">
        <stringvalue>compiz</stringvalue>
    </entry>
</gconf>

Replace `compiz' with `metacity', save and start  up again. If your system behaves like mine, everything should start up as normal, but with no desktop effects. From your desktop, you can open the settings for compiz and disable reflection, and then try compiz again. 

Failing that, there are lots of various %gconf.xml files in the /home/~l/.gconf/apps/compiz/general/ area tucked away which seem to list the plugins that compiz loads with under gnome. Perhaps you could edit these and deleting the entries of the form

<li type="string">
            <stringvalue>reflex</stringvalue>
        </li>
would do the trick but I've not really explored this myself.

Both of these are just hopefully intelligent guesses on my part - so please back up any filed you may edit and I may be totally wrong about whether these work - they're just things to try out if you're feeling desperate!

yossell

---

### Post by The Real Dave on 2009-11-21
> **yossell said:**
> I'm not sure if this will work but...

go to  /home/~/.gconf/desktop/gnome/session/required_components

(~ will be the name of your own home folder)

and try opening the file %gconf.xml there in a text editor. 

Hopefully, you see something like this:
<?xml version="1.0"?>
<gconf>
    <entry name="windowmanager" mtime="1258797724" type="string">
        <stringvalue>compiz</stringvalue>
    </entry>
</gconf>

Replace `compiz' with `metacity', save and start  up again. If your system behaves like mine, everything should start up as normal, but with no desktop effects. From your desktop, you can open the settings for compiz and disable reflection, and then try compiz again. 

Failing that, there are lots of various %gconf.xml files in the /home/~l/.gconf/apps/compiz/general/ area tucked away which seem to list the plugins that compiz loads with under gnome. Perhaps you could edit these and deleting the entries of the form

<li type="string">
            <stringvalue>reflex</stringvalue>
        </li>
would do the trick but I've not really explored this myself.

Both of these are just hopefully intelligent guesses on my part - so please back up any filed you may edit and I may be totally wrong about whether these work - they're just things to try out if you're feeling desperate!

yossell

Thank you :) I found those files, but I wasn't sure if I should mess with them :) That got me back in :)

---

### Post by yossell on 2009-11-21
Great! I'm pleased it worked - to tell you the truth, I wasn't sure whether you should mess with those files either :P

Best wishes

Yossell

---

