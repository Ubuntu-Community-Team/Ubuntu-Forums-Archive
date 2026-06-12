---
title: "Restoring key &quot;&lt;no value set&gt;&quot; original state"
date: 2011-04-05
forum: Desktop Environments
---

### Post by rhdinah on 2011-04-05
How does one set a key, e.g. an integer, to the <no value> state?

If you reset [erase] a given key that has an integer type and value of <no value> and then recreate a new key with the same name and type of integer there seems to be no value that is acceptable to the command line to set a value of <no value> ... any ideas? I've used the command line and gconf-editor to no avail.

Thanks! [Yes, I know this is a supergeek question!] :)

p.s. I do know how to reset the schema for this key, just not the null value!

---

### Post by Splooshie123 on 2012-03-20
I know this is extremely late but someone else might benefit.

If the entry existed already before you changed it, just right-click on it and select Unset.
It will disappear. If you quit gconf-editor and start it again, it should reappear with <no value> as the setting.

Anyway, unset is basically the same as deleting it. They have the same effect, I think.

---

