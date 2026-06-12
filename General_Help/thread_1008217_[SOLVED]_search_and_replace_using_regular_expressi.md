---
title: "[SOLVED] search and replace using regular expressions - please help!"
date: 2008-12-11
forum: General Help
---

### Post by uioreanu on 2008-12-11
I want to replace a string into a html file with another string. The string to be replaced is here

[HTML]<td><a href="mailto:info@abc.net" class="topmenu">Email</a></td>[/HTML]

and it should be replaced with:

[HTML]<td><a href="contact.php" class="topmenu">Contact</a></td>[/HTML]

so basically the href and the link text should be changed. I have tried using sed, who I call using this syntax:

```
sed -e 's/string_to_replace/string_to_replace/g' file.html
```

Thing is that I'm stuck in the search for the proper regular expression. Can any of you regexp gurus help me? 

Or Is there a way to tell sed not to use regular expressions? 

Thank you,
Calin

---

### Post by decoherence on 2008-12-11
No need for regular expressions if you just want to change one string for another.

Try this

```
sed 's!<td><a href="mailto:info@abc.net" class="topmenu">Email</a></td>!<td><a href="contact.php" class="topmenu">Contact</a></td>!g' file.html

```

Notice that we've replaced sed's default delimiter, "/" with a "!"

The delimiter can be whatever you like as long as it is consistent and doesn't appear in the source or replacement strings.

hth

---

