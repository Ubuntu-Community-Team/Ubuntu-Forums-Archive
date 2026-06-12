---
title: "Grep help please"
date: 2008-12-12
forum: General Help
---

### Post by Mb0742 on 2008-12-12
I have a lot of code which I need to go through which spans over a lot of scripts. I was hoping you guys could help me achieve an effective search using grep?

Thank-you for this help :)

Here is what I am looking for seshash: cGs1a256X2w3YXsoMnJ0aA==

using grep how can I get everything after the space and everything before the last '=' to show and that alone, so that the output is 'cGs1a256X2w3YXsoMnJ0aA=='   ? Thank you.

---

### Post by meson2439 on 2008-12-12
If your scripts are all in one folder, then

```
cat *.c | ls |grep 'cGs1a256X2w3YXsoMnJ0aA=='
```

I assume here the script is a c file. You can change that to any extension that you happen to use. If it produces nothing, try

```
cat *.c | ls |grep cGs1a256X2w3YXsoMnJ0aA
```

Hope that helps..

---

### Post by Mb0742 on 2008-12-12
Sorry. What I meant is I want to get that hash out of every file I throw at it so if the hash is bla== then the output would be bla I know which files I am using.

---

### Post by reality1011 on 2008-12-12
maybe something along the lines of awk -F":" '{print $2}' | cut -c <# of expected characters of key preceded by a - sign>

where -F means use this character to delimit columns in a row?

---

