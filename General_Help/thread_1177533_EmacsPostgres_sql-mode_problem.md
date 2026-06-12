---
title: "Emacs/Postgres sql-mode problem"
date: 2009-06-03
forum: General Help
---

### Post by gunksta on 2009-06-03
I am having a weird problem with emacs or postgres, I'm not entirely sure which. I have emacs-gtk installed. I am using emacs (in sql-mode) to work on a database I need for work.

Once I open up the .sql file, emacs recognizes it and jumps into sql-mode. I can then select my product (postgres) and start a sqli session. I then set my sesstion to *SQL*. So far so good. 

If I select a region of text, I can send it to the registered sqli session just fine. However, I can NOT send the entire buffer to the sqli session. When I do, it appears to run and I don't get any warnings or errors, but things are missing! You know, little things like tables and views that should be there and all the tables are empty. If I run the code section by section, it works. If I open up an eshell and run the .sql file against psql manually, everything works as expected.

Any ideas why emacs doesn't like my buffer?

thoughts / suggestions welcome.

---

### Post by gunksta on 2009-06-05
bump.

I've still got the problem and I haven't been real successful with solving it.

---

### Post by mmaug on 2009-09-20
I assume you're using emacs22 on Ubuntu.  I havent encountered the same issue but you're interaction pattern is different than mine.  What you are seeing sounds like a problem we used to have under w32 but not a real OS -- large chunks of text were getting stuck when pasted under w32 to another process but Linux is designed for that interaction style.  

I generally use the send to sql features to test code snippets.  I then either invoke the sql script from within the sql-interactive-mode buffer, or use a *shell* buffer to invoke the sql script.  

Random questions:
* have you tried pressing [ENTER] in the sql-interactive-mode buffer after you send the sql text to it?
* have you tried sending most of a sql buffer to the sql-interactive-mode and had the same behavior, or must it be the entire source buffer?

---

### Post by gunksta on 2009-09-22
Yes. I should have stated that I was running the default EMACS (gtk) in 9.04.

Random questions:
* have you tried pressing [ENTER] in the sql-interactive-mode buffer after you send the sql text to it?
* have you tried sending most of a sql buffer to the sql-interactive-mode and had the same behavior, or must it be the entire source buffer?

When the code is still running, I usually flip over to another virtual desktop and surf the Internet.  :-)

So no, I don't hit the enter key while stuff is running.  

I have tried grabbing large chunks of the buffer and sending it and things appear to work as expected. The problem *appears* to be tied to trying to run the entire buffer, although I did not develop any specific tests, this is just an informal observation.

I'll confess that I got frustrated with it and I have, for the time being, switched back to Vim. I figured if I was going to have to escape to the command-line to run things, I might as well use Vim. I'm curious to see if things are still funny in Karmic.

---

### Post by mmaug on 2009-10-04
My guess is it will still be funny under Karmic -- not sure whether Emacs 23 made the cut, but I can assure you I haven't made any changes to the process interaction in sql-mode.

I would recommend making sure the final newline gets sent.  If you select a range and send to sql, you generally select everything including the trailing newline.  Sending the whole buffer there may not be a newline on the last line.  This may result in the sent text actually getting submitted to the sql interpreter.

This is an area that I have targeted for further development (including the automatic submission on commands sent to sql).  The changes will be released with one of the future releases of Emacs, but will be compatible with Emacs 23.1 so you can start using it without waiting for an Ubuntu release.

---

