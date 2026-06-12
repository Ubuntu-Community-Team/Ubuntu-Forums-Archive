---
title: "Need to replace text with other text using SED or AWK or something"
date: 2009-04-26
forum: General Help
---

### Post by tomstealthports on 2009-04-26
Hello, I have a SED command which prints the output of the command to a file.  I want to either know how to convert this output to a string, so I can use it to replace the text in another file with this output, or just use SED to directly replace the text in file2 with this output.

So I want to change this:

#Old File

something or other

change a part of this line

blah blah
 
blah

#end of file

Into:

#New File

something or other

change a part of >"OUTPUT FROM SED"<

blah blah
 
blah

#end of file

Any ideas?  I think my brain can't handle much more googling today!

Thanks!

---

### Post by chrisamiller on 2009-04-26
If I'm reading this right, you want to change this line:

```
change a part of this line
```

to this line, substituting piped input from sed:

```
change a part of "OUTPUT FROM SED"
```

Here's a ruby one-liner:

```
<your sed command> | ruby -ne 'infile=File.new("oldfile.txt");infile.each{|line| if line =~ /this line/;line=line.gsub(/this line/,"asdf");end;puts line;}' >newfile.txt
```

And remember: TMTOWTDI

---

### Post by tomstealthports on 2009-04-26
Erm..Can't quite get it to work.  I have no clue what I'm doing.  What parts of your one liner do I need to replace?  Do I replace "oldfile.txt" with /name/of/path/to/myfile.txt (with no quotes) or "/name/of/path/to/myfile.txt" (with quotes?).  Also, am I telling ruby to search for specific text in a line with /this line/ (replacing /this line/ with /whatever is in the line I want to change/)

Please help with the syntax!

By the way, what is TMTOWTDI?  It better not be anything to do with man pages or google! (EDIT: Aaah, I see now)

Let me see if I can make it easier for myself...

What I want to do is replace the last 8 characters on line two of textfile2 with the first 8 characters from line one of file 1.  Does that make more sense?



EDIT:  Never mind, got it working!  Woohoo!  Now for the next bit...

Edit..Actually, I didn't get it to work with that method.  I did use some creative cat commands and template files to achieve the same result though.  Ugly as a bag of goblins, but it works!

Thanks for your help!

---

