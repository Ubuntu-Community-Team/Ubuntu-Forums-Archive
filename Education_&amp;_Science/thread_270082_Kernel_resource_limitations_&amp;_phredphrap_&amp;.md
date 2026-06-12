---
title: "Kernel resource limitations &amp; phred/phrap &amp; cap3"
date: 2006-10-02
forum: Education &amp; Science
---

### Post by devnulljp on 2006-10-02
I run into the 'Argument list too long' problem (described in linuxjournal: [http://www.linuxjournal.com/article/6060](http://www.linuxjournal.com/article/6060)) a lot as I'm doing genome sequencing and assembly using phred/phrap and recently also cap3. So, I often have hundreds of thousands of chromatogram files to move or work on at a time. 
I get around it with shell functions, which works fine most of the time, but when running an assembly with 1/2 million reads it's not possible to break up the input inbto smaller chunks.
The linxjournal article mentions rebuilding gthe kernel and editing MAX_ARG_PAGES in binfmts.h to allow more arguments passed to a single command. I tried this, but it didn't make any difference. Reading the thread on kernel.org it looks like MAX_ARG_PAGES is hard-coded elsewhere too. (I wonder if the author of the article was using gentoo or had some other way round this).
Question: has anybody managed to get round the  'Argument list too long' problem by recompiling the kernel? 
Alternatively, anyone had success running cap3 on large numbers of reads?

---

### Post by TorstenSeemann on 2008-07-07
A way around this is to use the find command.

find . -type f -name "*.ztr" -print0 | xargs -0 cat > ../filenames.txt

---

### Post by devnulljp on 2008-09-04
> **TorstenSeemann said:**
> A way around this is to use the find command.

find . -type f -name "*.ztr" -print0 | xargs -0 cat > ../filenames.txtFine if all I needed was a list of filenames? I was trying to do an assembly on a very large numebr of sequencing reads and cap3 keeps crapping out because of too many files. I don't see how find will help there, can you clarify?

---

