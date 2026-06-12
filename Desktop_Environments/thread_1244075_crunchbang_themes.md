---
title: "crunchbang themes"
date: 2009-08-19
forum: Desktop Environments
---

### Post by 19bab79 on 2009-08-19
i am having a lot of trouble getting my new themes installed on crunchbang. i have downloaded the tar.gz files. i first tried to install them as a tar.gz which didn't work. i then extracted it but when i go to install a new theme it allows me to browse the folders but not install the theme. i have put them into my .themes directory but it still doesn't seem to make a difference.

---

### Post by mcduck on 2009-08-19
what format the themes are when you extract them from the archive? Are they just directories with files in them, or are they in .obt format?

If they are just directories, placing them into ~/.themes should work just fine.

For .obt packages you should be able to click the "Install a new theme"-button in the Openbox Configuration Manager, browse to find your .obt file and click "OK".

---

### Post by snowpine on 2009-08-19
What kind of "themes" are you talking about? Openbox themes? GTK themes? GDM themes? Some other kind? Each gets installed in a different place using a different method...

---

### Post by 19bab79 on 2009-08-19
i finally got it to work. i converted the theme to .obt format. i thought i tried that last night but it didn't work. must have been something stupid i was overlooking. thanks for the replies.

---

### Post by urukrama on 2009-08-19
If you have an themename.obt theme, you can rename the file to themename.tar.gz and extract that into ~/.themes if you don't want to use Obconf.

If you extract a theme into ~/.themes while Obconf was running, you'll have to restart Obconf before you can select the theme with Obconf as it does not scan the themes folder for any new themes that might have been added manually.

---

