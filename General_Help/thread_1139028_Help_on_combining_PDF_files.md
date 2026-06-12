---
title: "Help on combining PDF files"
date: 2009-04-26
forum: General Help
---

### Post by kut77less on 2009-04-26
I used this tutorial to try to combine PDF files.
[http://www.zolved.com/synapse/view_content/2816a0/How_to_combine_and_separate_pdf_files_on_Ubuntu](http://www.zolved.com/synapse/view_content/2816a0/How_to_combine_and_separate_pdf_files_on_Ubuntu)


 It worked the first time I tried but then it stopped. 


I get this error 

> 
/home/whatiscreation/bin/pdftk_cat: line 2: cd: /home/whatiscreation/Documents/PDF/Volume: No such file or directory
Error: Failed to open PDF file: 
   *.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.



I really like this way of doing it, so how would I fix this

---

### Post by kaibob on 2009-04-26
I clicked on the link you provided but it didn't take me to a tutorial. Perhaps it would be better if you posted the command you are using.

---

### Post by kut77less on 2009-04-26
> **kaibob said:**
> I clicked on the link you provided but it didn't take me to a tutorial. Perhaps it would be better if you posted the command you are using.


here is the link Again sorry.

[http://www.zolved.com/synapse/view_content/28160/How_to_combine_and_separate_pdf_files_on_Ubuntu](http://www.zolved.com/synapse/view_content/28160/How_to_combine_and_separate_pdf_files_on_Ubuntu)

---

### Post by kaibob on 2009-04-26
The script in question is:

```
#!/bin/bash
cd ${1%/*}
outfile="00out.pdf"
if [ -f $outfile ] ; then
     rm -f $outfile
fi
/usr/bin/pdftk *.pdf cat output $outfile
```

The script is designed to be used with the Nautilus open-with command. At what point do you see the error message shown in your original post? I tried the script, and it worked fine in all instances. 

BTW, the variable in the second line of the script should be quoted--otherwise it won't work with directories that contains spaces.

```
cd "${1%/*}"
```

---

### Post by lyall on 2009-04-26
Hi kut77less

have you tried pdfsam
it is a graphical interface program

I justed installed and tried it. Merged four pdf files together with no problems.
It left the four original file and created one new file


hope this help
alway check Synaptic for apps that might work :P

Good Luck and have fun

---

### Post by kut77less on 2009-04-27
> **kaibob said:**
> The script in question is:

```
#!/bin/bash
cd ${1%/*}
outfile="00out.pdf"
if [ -f $outfile ] ; then
     rm -f $outfile
fi
/usr/bin/pdftk *.pdf cat output $outfile
```

The script is designed to be used with the Nautilus open-with command. At what point do you see the error message shown in your original post? I tried the script, and it worked fine in all instances. 

BTW, the variable in the second line of the script should be quoted--otherwise it won't work with directories that contains spaces.

```
cd "${1%/*}"
```



Thanks for all your help. All I did is put quotations around the script, and it worked. The only thing I need to is know how to unsecure PDF files.

---

