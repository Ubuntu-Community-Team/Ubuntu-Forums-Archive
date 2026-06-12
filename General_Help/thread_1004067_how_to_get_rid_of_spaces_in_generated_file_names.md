---
title: "how to get rid of spaces in generated file names"
date: 2008-12-06
forum: General Help
---

### Post by meg23 on 2008-12-06
I have all these files on my desktop that I want to get rid of the spaces in their names. Here is a listing of the files:

```
Mumbai attacks- police admit there were more than ten attackers - Telegraph.png
Obama asks Americans to discuss health reform  Triage.png
Obama picks general to lead veterans affairs  Reuters.png
Page Image.png
Pierce Meets With Police; No Decision on Charges - NYTimes.com.png
```

How do I search for files like this and replace the spaces with an underscore?

---

### Post by inxygnuu on 2008-12-06
what do you mean? do you want to rename them? if so:

right click, go to properties, and in the name textbox, rename the files.

best regards,
3v4n;)

---

### Post by meg23 on 2008-12-06
I mean using the terminal and having it automated.

---

### Post by kaibob on 2008-12-06
The following will do what you want:

```
for file in * ; do mv "${file}" "${file// /_}" ; done
```

As always, test this on copies of files just to make sure that it does what you want.

---

### Post by meg23 on 2008-12-06
dude you rock major thanks

---

### Post by reality1011 on 2008-12-06
> **kaibob said:**
> The following will do what you want:

```
for file in * ; do mv "${file}" "${file// /_}" ; done
```

As always, test this on copies of files just to make sure that it does what you want.

As an aside, I'm not sure what you mean by "search for files like this." I assume you just want to rename the files.



I was actually trying to figure this out myself... couldnt figure out how to do it in 1 line though... nice...

only thing I would add is :

for file in **[COLOR="Red"]*\ *[/COLOR]** ; do mv "${file}" "${file// /_}" ; done

---

