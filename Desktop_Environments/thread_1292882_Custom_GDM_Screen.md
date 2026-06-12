---
title: "Custom GDM Screen"
date: 2009-10-16
forum: Desktop Environments
---

### Post by biozenunity on 2009-10-16
I am making a custom GDM screen and would like to have a quote that is randomly changed every login. Is this possible and if so how would I go about it? Thanks.

Edit: Also is there any way to detect the users monitor and supply a 4:3 or 16:9 background accordingly?

---

### Post by biozenunity on 2009-10-20
OK, I have figured it out. Add this to your gdm.xml

```

<item type="label">
    <text></text> #make note of what line number this is
</item>

```Then add this to a bash script somewhere pre GDM in the startup sequence
# is the line number you made note of in your gdm.xml file

```

num=$[ ( $RANDOM % x )  + 1 ] #x being the number of random quotes you want
if [[ $num == "1" ]] 
   then
      sed '#s/.*/<text>quote</text>/' -i /path/to/gdm.xml
fi

```

---

