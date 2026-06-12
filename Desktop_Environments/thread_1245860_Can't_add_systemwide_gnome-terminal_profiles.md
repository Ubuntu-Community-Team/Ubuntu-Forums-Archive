---
title: "Can't add systemwide gnome-terminal profiles"
date: 2009-08-21
forum: Desktop Environments
---

### Post by djchester on 2009-08-21
Hi 

I'm trying to create a system wide profile for gnome-terminal that is not located on a home directory to use when certain settings are sourced for a certain application. Pretty much like the Default but with the name "test" but I'm not succeeding. I _don't_ want to replace the Default.

What I have done so far is this:
Made changes on a test client (as root) so that the Default profile looks like I want it to look. Then:

gconftool-2 --dump /apps/gnome-terminal/profiles/Default > default.xml
sed -i `s/\/Default\//\/test\//g' default.xml
mv default.xml test.xml

On a fresh client:
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load=test.xml

Then when logged in as a ordinary user I run:
gnome-terminal --window-with-profile=test

However it seems it does not find the profile. It is not appearing in the profile list in gnome terminal either. If I look in gconf-editor it seems to be imported but perhaps something obvious is missing.

Any ideas are appreciated. Also if you have ideas on a better forum to post this I will be grateful. gnome-terminal is after all not Ubuntu specific.

If this is not possible I will have to use xterm (ugly) or multi-gnome-terminal (not standard) which does not need profiles but have great startup options which makes life a lot easier. 

Best Regards

_____________________________________________
djchester

---

