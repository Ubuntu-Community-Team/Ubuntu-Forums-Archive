---
title: "[SOLVED] Limit the characters in HTML"
date: 2008-12-17
forum: General Help
---

### Post by CrusaderAD on 2008-12-17
Does anyone know how to limit the numbers of characters in HTML? I have something like this:

```
<center>ep1image</center><br>
<center><font color=000000>ep1name</font></center><br>
ep1description<br>
ep1link<br><br>
```

I'd like ep1description to be limited to about 200 characters.

---

### Post by pedro_orange on 2008-12-17
Yes if you use something like a textbox/area/form.

Your question is rather ambiguous and you need to tell us what you're trying to achieve with some context.

---

### Post by CrusaderAD on 2008-12-17
I just want that desription limited to 200 characters. I don't want a text box or anything around it.

---

### Post by S_e_P_p on 2008-12-17
As html is static I don't see any sense in 200 caracter limit.

If you use another programming language to fill this you could limit your variable to 200 characters.

---

### Post by pedro_orange on 2008-12-17
Well if you're hard coding the description as just an area of text within your HTML there is nothing that can do what you want. 
(From what I understand of what you're asking)

---

### Post by CrusaderAD on 2008-12-17
> **S_e_P_p said:**
> As html is static I don't see any sense in 200 character limit.

If you use another programming language to fill this you could limit your variable to 200 characters.

I'm am also using VB6... how do I limit the variable?

---

### Post by S_e_P_p on 2008-12-17
Dim S As String * 20

will limit S to 20 characters

[http://www.cpearson.com/excel/SizeString.htm](http://www.cpearson.com/excel/SizeString.htm)

---

### Post by pedro_orange on 2008-12-17
> **raptormanad said:**
> I'm am also using VB6... how do I limit the variable?

```
Dim MyString As String * 200
```

Tells VB to limit you to 200 characters in the string variable MyString.

---

### Post by CrusaderAD on 2008-12-17
I tried your suggestions using my variables...

Dim ep1description As String * 200

But it still doesn't work... it loads a ton of text.

---

### Post by CrusaderAD on 2008-12-17
I'm not sure if this makes a difference... but it's a variable which pulls text from a sql table.

---

### Post by S_e_P_p on 2008-12-17
You can use the substring() function.

```

Dim tmpstring as String
tmpstring = ep1description.Substring(0,20)

```


Starts at pos 0 to 20

Greets,
SePp

---

### Post by CrusaderAD on 2008-12-17
I forgot, I'm doing a replace in the vb script:

ebody = Replace(ebody, "ep2description", RS6("description"))

How would I limit that?

---

### Post by CrusaderAD on 2008-12-17
I got it. I just put the RS6("description") in a variable and limited that. Thanks!

---

