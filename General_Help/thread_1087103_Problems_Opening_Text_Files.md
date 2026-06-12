---
title: "Problems Opening Text Files"
date: 2009-03-04
forum: General Help
---

### Post by crokett on 2009-03-04
I have a weird problem trying to open text files.  These files are logs from my customers' network switching equipment.  Gedit says it doesn't know what kind of encoding to use to open them.  I can cat the files just fine and can open them on a Windows system. I tried piping the cat from one to echo into another.  When I opened the second file Gegit showed a bunch of what I assume are hex codes, then shut itself down.

  Why is this happening and how can I fix it?  I need to look at these files to do my job.  It doesn't happen on all of them, just some.  I've looked at the ones where it happens and can't see a difference between those and the ones that have no problem.

If it helps when I run the file command I get this:

```

dr2.txt.cisco.txt: ASCII English text, with CRLF line terminators

```

Same command on a file that works shows me this:

```

A02DMDS2.txt.cisco.txt: ASCII English text, with CRLF, CR line terminators

```

I am assuming the problem is the lack of CR line terminators. Any suggestions for a better editor that won't get confused?  These files are captures from either Hyperterminal or Putty, mostly on Windows.

---

### Post by crokett on 2009-03-04
I am going to try gvim.  It has some features I need such as bookmarking, tab support and a few others.  It also isn't choking on the problem files.

---

### Post by heindsight on 2009-03-04
> **crokett said:**
> I have a weird problem trying to open text files.  These files are logs from my customers' network switching equipment.  Gedit says it doesn't know what kind of encoding to use to open them.  I can cat the files just fine and can open them on a Windows system. I tried piping the cat from one to echo into another.  When I opened the second file Gegit showed a bunch of what I assume are hex codes, then shut itself down.

  Why is this happening and how can I fix it?  I need to look at these files to do my job.  It doesn't happen on all of them, just some.  I've looked at the ones where it happens and can't see a difference between those and the ones that have no problem.

If it helps when I run the file command I get this:

```

dr2.txt.cisco.txt: ASCII English text, with CRLF line terminators

```

Same command on a file that works shows me this:

```

A02DMDS2.txt.cisco.txt: ASCII English text, with CRLF, CR line terminators

```

I am assuming the problem is the lack of CR line terminators. Any suggestions for a better editor that won't get confused?  These files are captures from either Hyperterminal or Putty, mostly on Windows.

In the unix world, lines in text files are terminated by LF characters, while in the dos (and by extension windows) world lines are terminated by the CRLF character pair.

I just created a file with CRLF line endings and gedit opened it without any complaints, so I don't think that alone is your problem. Perhaps there are other non-printing characters in your file that confuse gedit about the file's encoding.

You can easily convert between dos and unix text formats by installing tofrodos:
```
sudo apt-get install tofrodos
```
and then doing:
```
todos < foo_unix.txt > foo_dos.txt
```
or
```
fromdos < foo_dos.txt > foo_unix.txt
```
Try it and see if it helps, but I'm not sure it will.

What you could try is to use tr to delete all nonprinting characters like:
```
tr -cd '[:space:][:print:]' < file_in.txt > file_out.txt
```
and see if that helps.

Another option would be to simply use a different text editor, one that is less easily confused ;)

---

### Post by Claus7 on 2009-03-04
Hello,

this is what I was going to advice you to do. Some files that I opened with gedit, where just unreadable, whereas with vim I could read them. In case you face more problems with encoding, this is what I did with the hellenic language, yet the idea of identifying and converting a file's encoding is the same:
[http://ubuntuforums.org/showthread.php?t=748249&highlight=encoding](http://ubuntuforums.org/showthread.php?t=748249&highlight=encoding) 

Regards!

---

### Post by ryan.nabinger on 2009-03-04
Once you learn vim you can never go back ...

now all that happens when I edit in a "normal" text editor is random "jjjjkjllldwdw5jddddjj3dd :wq"

hahaha

---

### Post by heindsight on 2009-03-04
> **ryan.nabinger said:**
> Once you learn vim you can never go back ...

now all that happens when I edit in a "normal" text editor is random "jjjjkjllldwdw5jddddjj3dd :wq"

hahaha

:D hear hear!

---

### Post by crokett on 2009-03-04
> **ryan.nabinger said:**
> Once you learn vim you can never go back ...

now all that happens when I edit in a "normal" text editor is random "jjjjkjllldwdw5jddddjj3dd :wq"

hahaha

So I'm told but I do a lot of cutting, pasting emailing, etc in my job and all those require a mouse anyway.  So if I have to be using a mouse then it appears gvim will do what I want.

---

