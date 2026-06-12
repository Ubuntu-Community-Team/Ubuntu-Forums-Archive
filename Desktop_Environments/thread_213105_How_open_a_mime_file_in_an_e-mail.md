---
title: "How open a mime file in an e-mail?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by dgermann on 2006-07-10
Hi--

I am getting e-mails from a correspondent with part of them in mime format. For instance, this part starts like this:

```

--=_alternative 004FF9948525719D_=--

--=_mixed 004FF9928525719D_=
Content-Type: application/octet-stream; name="B&I Processing 
Guide&ApplicationChecklists MAY 06.doc"
Content-Disposition: attachment; filename="B&I Processing 
Guide&ApplicationChecklists MAY 06.doc"
Content-Transfer-Encoding: base64

0M8R4KGxGuEAAAAAAAAAAAAAAAAAAAAAPgADAP7/CQAGAAAAAAAAAAAAAAAFAAAAXgIAAAAA
AAAAEAAAYAIAAAEAAAD+////AAAAAFUCAABWAgAAVwIAAFgCAABfAgAA////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////
///////////////////////////////////spcEAIWAJBAAA8BK/AAAAAAAAEAAAAAAABgAA
JEgAAA4AYmpialytXK0AAAAAAAAAAAAAAAAAAAAAAAAJBBYAnScEAD7HAAA+xwAApz8AAAAA
AAB8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD//w8AAAAAAAAAAAD//w8AAAAAAAAAAAD//w8A
AAAAAAAAAAAAAAAAAAAAAKQAAAAAABgFAAAAAAAAGAUAABgFAAAAAAAAGAUAAAAAAAAYBQAA

```

So how do I open and read this part?

I have found a Windoze program that will open it, but I shouldn't have to resort to that, right? ;) 

Thanks!

---

### Post by scxtt on 2006-07-10
what email program are you using? ... looks like someone sent you a *.doc file (and not necessarily as an attachment, or some sort of inline-attachment) ...

filename="B&I Processing Guide&ApplicationChecklists MAY 06.doc"

---

### Post by dgermann on 2006-07-12
scxtt--

Thanks!

The e-mail program I am using is plain text one, Tapcis6 by name, an old DOS based program.

If I use another DOS program called xferpro, I can translate it on an old Win95 machine I have. I would much prefer to not have to rely on the old machine, let alone get up and go into another room to use it! :(  Ubuntu is better, yes?

Anyway, I use that program to translate mime base 64 files, so I suspect that is what I have here.

If anybody knows, what handles that in linux?

Thanks, scxtt!

---

### Post by scxtt on 2006-07-12
just cause i'm curious, why are you doing it that way? -- i can't see any advantage to trying to view a *.doc file from the command line ... but i can understand viewing your mail from the command line :)

---

### Post by dgermann on 2006-07-13
scxtt--

Tapcis6, my e-mail program, reads only ascii text. I suspect it is like pine, although I have never used pine.

So what I have gotten is an e-mail that says, in effect, "Hi Doug. Here's the file I promised you. Joe." Then at the bottom of the e-mail is that stuff I copied above. There is no .doc file there at all, just that mime-encoded stuff.

Does that make it any easier to imagine what I am seeing? Not sure how to explain it....

So I am not looking at it from the command line, I just can't decode it in the e-mail client, so I need some linux solution for decoding it and giving me the inline .doc files.

Thanks, scxtt!

---

### Post by scxtt on 2006-07-13
i don't know what to tell you ... if you don't have a way to "save attachment" then it looks like you're out of luck ...

looking at the code you posted, it's a "application/octet-stream" mime type, with a "name="B&I Processing 
Guide&ApplicationChecklists MAY 06.doc" which is why i brought up .doc files ... what you're seeing is the unencoded microsoft word format that Tapcsi6 can't process ...

so unless Tapcis6 has a "octet-stream" plugin or you can save that data as a .doc file - i think you're SOL ...

---

### Post by dgermann on 2006-07-14
scxtt--

Thanks. I can still open it in DOS (app called xferpro), but that is a bit cumbersome.

Thanks for your help, scxtt!

---

### Post by jdschwa on 2008-03-02
I recently ran into this problem as well. uudeview worked for me.

---

### Post by dgermann on 2008-03-02
jdschwa--

Ahh!

I grabbed it and it worked very well. Thanks for letting us know about this!:popcorn:

---

