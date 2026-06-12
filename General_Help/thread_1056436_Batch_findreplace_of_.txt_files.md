---
title: "Batch find/replace of .txt files"
date: 2009-01-31
forum: General Help
---

### Post by camerong on 2009-01-31
hey, I need some help again.

Basically, I have a lot of .txt's in a folder that all have some text as follows: (just the general format, obviously not the real text)

ONEONEONEblahTWOTWOTWOblahTHREETHREETHREE

I need to open all of them and remove the ONEONEONE, the TWOTWOTWO, whatever the blah is that is between the one and the two, and the THREETHREETHREETHREE.

In other words, I just want to leave the second blah.

For clarification, I don't know what the blahs are, and they change. This is kinda like a puzzle.

Yeah, I'm sure this involves cat or grep or some command, but not sure.

Thanks for any help. I know it's a bizarre question.

---

### Post by geirha on 2009-01-31
A more realistic sample could yield a better solution, but based on the information you've given so far, something like this should do the trick:
```
sed -i~ -r 's/ONEONEONE.*TWOTWOTWO(.*)THREETHREETHREE/\1/' *.txt
```

It will do the change in-place, but with backups (ending wiht ~) of the originals.

---

### Post by camerong on 2009-01-31
The .txt files contain html code, and, in the example below, I'm attempting to remove "<!DOCTYPE", "<!-- Page 1 -->", everything between the previous two strings, as well as "</BODY></HTML>"

```
sed -i~ -r 's/<!DOCTYPE.*<!-- Page 1 -->(.*)</BODY></HTML>/\1/' *.txt
```

It returned:

> sed: -e expression #1, char 42: unknown option to `s'

I think character 42 is between "(." (using gedit's column counter, but I'm assuming it's referring to one of those.)

also, what is the meaning of "s/"?

---

### Post by geirha on 2009-01-31
The problem is that / is a special character for sed in the above case, so the /'es in </BODY></HTML> would need to be escaped (<\/BODY><\/HTML>). However, sed typically works on a line by line basis, but I doubt the HTML code in that file is all on one line. You'll probably need to parse that file as html, which is not as easy as a sed-replacement.

Depending on exactly what you want to extract, you might be able to use sed though, by first removing all newlines, so that it all becomes one line that sed can handle.

---

### Post by camerong on 2009-02-01
```
cd to directory
find / -type f -name '*.html' -exec sed -i 's/\n/ /g' {} ;
```

I tried the above and got: 

> find: missing argument to `-exec' (now attempting to remove all newlines and replace with a space)

---

### Post by geirha on 2009-02-01
-exec must be closed with an escaped semicolon (\;).

I think this might do the trick though. This replaces '\n's with '\r's, then sed is run, extracting everything between <!-- Page 1 --> and </BODY>, then the '\r's are changed back to '\n's. If the html files already contain '\r's, just use a different char. The original .html-file remains untouched, and the resulting file is named .html.new
```

find -type f -name "*.html" -exec bash -c "tr '\n' '\r' < '{}' | sed -r 's,.*<.-- Page 1 -->(.*)</BODY>.*,\1,' | tr '\r' '\n' > '{}.new'" \;

```

---

### Post by camerong on 2009-02-01
It worked!

Thanks a ton.

---

### Post by nulall on 2011-01-20
I can't really get this figured out properly but I have a similar issue.  I want to remove from all html files in a directory the following code:

width="###" height="###"

where the ### varies widely.  Any suggestions?

---

### Post by Vaphell on 2011-01-20
```
echo 'something width="30" height = "1000em" something else' | **sed 's/width\s*=\s*"[^"]*"\s*height\s*=\s*"[^"]*"//g'**
``` seems to work
it assumes that they appear together in exact order
if you need to delete any occurence of either width of height then
```
echo 'something width="30" junk height = "1000em" something else' | **sed -r 's/(width|height)\s*=\s*"[^"]*"//g'**
```

combine the sed part with the example above (find ... -exec ...), it should work but don't change the files in place right off the bat, check first if it's safe.

---

