---
title: "Installing from Ubuntu Source Repos"
date: 2006-09-05
forum: Desktop Environments
---

### Post by LadyDoor on 2006-09-05
Hello,

I'm trying to install Surfraw from the Ubuntu source repos so that I can add my own elvi (or try to). This detail is unimportant. What is important is this error message, spit out by make.

```

Making all in elvi
make[1]: Entering directory `/home/door/misc/src/surfraw-2.1.1/elvi'
cat alioth altavista amazon ask austlii bbcnews cddb cia cite cnn currency cve debbugs debcontents deblists deblogs debpackages debpts deja dmoz ebay etym excite fast foldoc filesearching freebsd freedb freshmeat jake google happypenguin imdb scpan slinuxdoc leodict netbsd openbsd pgpkeys pubmed rae rfc rhyme slashdot sundocs sourceforge stockquote scaleplus sunsolve thesaurus translate w3css w3html w3link w3rdf webster wetandwild wikipedia woffle xxx yahoo yubnub|egrep '^#.*elvis:'|sed 's/^.*elvis: *//'|sort > surfraw_elvi.list
make[1]: Leaving directory `/home/door/misc/src/surfraw-2.1.1/elvi'
make[1]: Entering directory `/home/door/misc/src/surfraw-2.1.1'
rm -f surfraw surfraw.tmp
sed 's,@bindir\@,/usr/local/bin,g; \
             s,@mandir\@,/usr/local/man,g; \
             s,@VERSION\@,2.1.0,g; \
             s,@prefix\@,/usr/local,g; \
             s,@ELVIDIR\@,/usr/local/lib/surfraw,g; \
             s,@sysconfdir\@,/usr/local/etc,g' surfraw.IN >surfraw.tmp
sed: -e expression #1, char 214: unterminated address regex
make[1]: *** [surfraw] Error 1
make[1]: Leaving directory `/home/door/misc/src/surfraw-2.1.1'
make: *** [all-recursive] Error 1

```

Does anyone know what's going on there?

Thanks,
Door

---

### Post by piroshki on 2006-09-05
Hi,

I don't know much about compiling packages from source, but it seems to be complaining about the sed command.

A shot in the dark here... what happens if you open "Makefile", find these lines:
```

         sed 's,@bindir\@,${bindir},g; \
              s,@mandir\@,${mandir},g; \
              s,@VERSION\@,${VERSION},g; \
              s,@prefix\@,${prefix},g; \
              s,@ELVIDIR\@,${ELVIDIR},g; \
              s,@sysconfdir\@,${sysconfdir},g' $< >$@.tmp

```

and remove the backslashes on the end of each line?

Might be worth backing the file up before-hand :)

---

### Post by LadyDoor on 2006-09-06
Hmmm...I tried removing the backslashes, but I still got the same error. Any other ideas?

--Door

---

### Post by Desman on 2006-09-06
Well, I'd say that removing backslashes ain't such a good idea - they just mean that the argument string is continued on the next line. What you get is complaint from sed that the regexp is not terminated properly. looks like sed command looks like ```
sed 's,@<thing-to-find>\@,<thing-to-insert-instead>,g;'
```, where the semicolon is obviously a regexp terminator.
What you can try to do is add the semicolon in the end of the string argument to sed, i.e. edit 
```

         sed 's,@bindir\@,${bindir},g; \
              s,@mandir\@,${mandir},g; \
              s,@VERSION\@,${VERSION},g; \
              s,@prefix\@,${prefix},g; \
              s,@ELVIDIR\@,${ELVIDIR},g; \
              s,@sysconfdir\@,${sysconfdir},g' $< >$@.tmp

```

so it looks like this:
```

         sed 's,@bindir\@,${bindir},g; \
              s,@mandir\@,${mandir},g; \
              s,@VERSION\@,${VERSION},g; \
              s,@prefix\@,${prefix},g; \
              s,@ELVIDIR\@,${ELVIDIR},g; \
              s,@sysconfdir\@,${sysconfdir},g[COLOR="Red"]**;**[/COLOR]' $< >$@.tmp

```

Hope it will work for you!

---

### Post by LadyDoor on 2006-09-06
```

sed 's,@bindir\@,/usr/local/bin,g; \
             s,@mandir\@,/usr/local/man,g; \
             s,@VERSION\@,2.1.0,g; \
             s,@prefix\@,/usr/local,g; \
             s,@ELVIDIR\@,/usr/local/lib/surfraw,g; \
             s,@sysconfdir\@,/usr/local/etc,g;' surfraw.IN >surfraw.tmp
sed: -e expression #1, char 215: unterminated address regex
make[1]: *** [surfraw] Error 1

```

Here's the new version of the error after adding the semicolon to the end--it moved the character in error up by one (it's 215 now instead of 214). Any ideas? (P.S.:  That only changed anything after editing Makefile, Makefile.in, and Makefile.include).

If anyone has anything, I'm eager to hear it.
--Door

---

### Post by cstudent on 2006-09-06
I'm not that familiar with sed, but I would try separating the > from the output file with a space.

surfraw.IN > surfraw.tmp

---

### Post by LadyDoor on 2006-09-06
I still got the same error. Would whoever packaged this for Ubuntu know? After all, the non-source package works fine (assuming you don't want to add anything to it).

If anybody knows anything about this, please let me know!

Thanks,
Door

---

### Post by piroshki on 2006-09-06
If I paste the following into a terminal on my machine:
```

sed 's,a,1,g; \
	s,e,2,g; \
	s,i,3,g' /etc/debian_version

```

I get:
```
sed: -e expression #1, char 29: unterminated address regex

```
Which looks like the same error you are getting.

But if I remove the backslashes:
```

sed 's,a,1,g;
	s,e,2,g;
	s,i,3,g' /etc/debian_version

```
sed returns successfully.

I'm not sure that bash needs the backslash to continue on a new line if the sed script is already encased in single quotes. Can anyone confirm?

Changing it in "Makefile" was wrong, looks like the changes should be in "Makefile.in". 

Removing the backslashes in Makefile.in changes the error to this:
```

/bin/sh: -c: line 0: unexpected EOF while looking for matching `''
/bin/sh: -c: line 1: syntax error: unexpected end of file

```

So I think sed can't handle the backslashes, but the sed command is being passed as a single command string to /bin/sh, which does requires them.

I managed to compile it by putting the whole command on one line in Makefile.in. Changing this:
```

        sed 's,@bindir\@,${bindir},g;
             s,@mandir\@,${mandir},g;
             s,@VERSION\@,${VERSION},g;
             s,@prefix\@,${prefix},g;
             s,@ELVIDIR\@,${ELVIDIR},g;
             s,@sysconfdir\@,${sysconfdir},g' $< >$@.tmp

```
to this:
```

        sed 's,@bindir\@,${bindir},g;s,@mandir\@,${mandir},g;s,@VERSION\@,${VERSION},g;s,@prefix\@,${prefix},g;s,@ELVIDIR\@,${ELVIDIR},g;s,@sysconfdir\@,${sysconfdir},g' $< >$@.tmp

```

---

### Post by LadyDoor on 2006-09-06
That did it! Brilliance!

Thank you very much!

--Door

---

### Post by piroshki on 2006-09-06
No problem :)

Actually, a cleaner way to do it would be to replace the single quotes around the sed script with double quotes.

---

