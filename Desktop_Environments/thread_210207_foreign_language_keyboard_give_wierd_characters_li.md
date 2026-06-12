---
title: "foreign language keyboard give wierd characters like &quot;¿quÃ© tal estÃ¡s?&quot;"
date: 2006-07-06
forum: Desktop Environments
---

### Post by lefty.crupps on 2006-07-06
In KDE there is a way to add another keyboard layout. When active, there is a flag in my System Tray that I can click on and it cycles through the flags of various languages that I have set up. Ok, well only Spanish and English so far

When I have it set to Spanish I can type the accents and other things just fine. But if I save file names or metadata information (for music) with these characters it produces incorrect characters in that name/data. Same if I send an email in GMail using Firefox; it looks fine on my screen, but when I hit send I get all kinds of odd characters (and it drives the recipient nuts)(his emails appear flawless on my screen)

For example:
"¿quÃ© tal estÃ¡s?" should read
"que' tal esta's?" (with accents on the letters, not apostrophies)

and "Â¿dos aÃ±os?" should read
"dos an~os" (with a tilde on the 'n')

Where is this error? Is it a Unix/DOS mismatch somewhere (even though its all Linux on my machine, and through GMail too i believe). Is there a Unicode checkmark box thing in KDE that I am missing? ](*,) It seems to me there is a standard not being supported somewhere.

Thanks for any information or pointers

---

### Post by knn on 2006-09-02
Gmail has an outgoing message encoding setting, which can be set to utf-8 (unicode) or "default"
Here's what Gmail says about this:
> 
	
Why would I want to send my messages in UTF-8?
Each time you send a message, Gmail automatically selects an appropriate encoding for the language(s) in which you've composed your mail. It's possible, however, that the recipient may not be able to properly view the message you've sent.

If your contacts are having trouble viewing messages you've sent them, we recommend using 'UTF-8' (Unicode) for all outgoing mail. UTF-8 is a standard encoding that's accepted by many email clients. 

Try both (utf-8 should work)

As for the filenames thing, I don't have problems with ext3, but filenames with int. characters that are on a fat32 drive appear incorrectly in linux (they're fine on Win), I don't know how to fix that

---

