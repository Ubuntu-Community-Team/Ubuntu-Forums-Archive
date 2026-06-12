---
title: "evolution should import .pst files"
date: 2009-05-06
forum: Desktop Environments
---

### Post by sparky-steve on 2009-05-06
Hello,

According to [http://library.gnome.org/users/evolution/stable/importing-mail-and-settings.html.en_GB](http://library.gnome.org/users/evolution/stable/importing-mail-and-settings.html.en_GB) evolution can import .pst files - however, when I try, I get as far as selecting my pst file, but it wont go any further, as if it doesn't recognise the format.

Can anyone point me in the right direction?

Thanks
SS

---

### Post by johnzollo on 2009-05-08
This is a known issue.  I hope someone is working on it.  (there may be a work-around, but I can't get it to work... so good luck!)

more info (another thread):
[http://ubuntuforums.org/showthread.php?t=1134714&highlight=pst](http://ubuntuforums.org/showthread.php?t=1134714&highlight=pst)

sincerely,
john

---

### Post by johnzollo on 2009-05-08
[SIZE="4"]IF ANYONE KNOWS A SUCCESSFUL WAY OF BUILDING EVOLUTION TO SUPPORT PST-IMPORT I WOULD LOVE TO KNOW!!![/SIZE]

I've tried building it with a debdiff on launchpad.  I can see the option for pst import, but it doesn't work.  DOES ANYBODY HAVE ANY IDEAS???

PLEASE!!!


Thanks.

Sincerely,
John

---

### Post by jflaker on 2009-05-08
Do you have gmail?
Set up your gmail to accept imap
create an imap account in Outlook and then move your folders one by one over to gmail

Boot up Ubuntu

Set up evolution with a gmail imap account and move your folders back over..

that was my workaround...depending on your mail size, it may take a while, but you get to keep your mail.

---

### Post by technocp on 2009-05-09
Above idea, I suppose may not be suitable with people using slow internet connection.

---

### Post by fballem on 2009-05-09
A question - have you already migrated from a Windows machine? The reason that I ask is that if you have not, then you can use Thunderbird to convert the Outlook mail. In addition, you will have to export your contacts, and your calendar files. 

Once converted, copy the mbox, contacts, and calendar files to an external drive.

After installing ubuntu and running evolution once, you should be able to copy the mbox folders into ~/home/.evolution/mail/local and import the contacts and calendar entries.

If you don't have Windows and Outlook running, then there is a program called Readpst that may be helpful. I haven't used it, but there is a thread here that may help: [http://ubuntuforums.org/showthread.php?t=39627](http://ubuntuforums.org/showthread.php?t=39627)

Hope this helps,

---

### Post by sparky-steve on 2009-05-09
Hi

Personally, I still have an XP machine in vmware so I could do all of that.

I have used readpst, and it "kinda works" but there was lots of errors; I think mainly to do with attachments or inline photos and the like.

My main point remains; One of the features of evolution is the importing of pst files; I shall try to swim upstream and see what I can find out.

SS

---

### Post by itsjustarumour on 2009-05-09
I'm still struggling to find a way to import PST files into Evolution.  This was advertised all over the place by Ubuntu prior to the release of 9.04... suffice to say on this occasion I'm feeling rather cheesed off and let down by Mr Shuttleworth and Co.  :-(

---

### Post by kerneloftruth on 2009-06-21
**itsjustarumour** I feel your pain,

but you also have to think about the cause why this problem exists:

pst is a proprietary format for which microsoft won't wholeheartedly allow other apps than theirs access to

[http://en.wikipedia.org/wiki/.pst]("http://en.wikipedia.org/wiki/.pst")

so blame them :(

I'm confident that it will work at some time in the future but as a general rule this will take some time

so provide as much feedback as possible at launchpad.net if it's working even only partially

**@jflaker:**

interesting approach - I'll see if I can get that to work

or alternatively I'll take a look at thunderbird 

thanks ! :KS

---

### Post by evargasp@gmail.com on 2009-11-20
Estimados después de seguir mil recetas en Internet y perder mucho tiempo, llege a la Importación de Evolution, la cual tiene la opción de Importar archivos Outlook personal folder (PST) y funciona súper bien con un pst de 1,2 GB.
Mi sistema es Ubuntu 9.10 de 64 bits y el Evolution 2.28.1.
Ojalá les sirva

Saludos =D>=D>=D>

---

### Post by alecwk on 2009-12-23
Sometimes we have to go round and round only to find that the solution is right in front of us. And this just happened to me. 

Importing Outlook .pst file into Evolution is as simple as go to Evolution and Import it!!!

I am using Evolution 2.28.1 bundled with Ubuntu Karmic. Start your Evolution, go to File>Import. A window will pop up, choose "import a single file", choose the .pst file you want to import and tick what you want to import and press forward. As simple as that. 

You may have to try a few times importing the .pst file before you get all your files imported. I had a somewhat corrupted .pst file, I can't even import to another Outlook. The Evolution did it well enough. Its an Evolution!!

---

### Post by sdsmall on 2009-12-29
I have imported .pst into evolution under Ubuntu 9.1 - just follow the menu clicks.  If you have a BIG .pst, it might take some time for the select command to complete - just wait it out!

I have seen a post that details how to change Evolution to import contacts directly into your personal folder rather than the Mccloud or whatever it is called.  I can't seem to find it now.  Does anyone know where it is?

---

### Post by HarleyPacker on 2011-02-19
I too have found that Evolution 2.28, in my Karmic 9.10 release CD install, does indeed directly import PST files.  Mine was almost 450M and it did it just fine.

Why they took that out in later distributions of Evolution I can't imagine.... I plan to keep my 9.10 release CD forever just in case I need to ever re-import at a later date.   Despite backups, things don't always go as planned and I haven't been able, for work reasons, to totally abandon Redmond ties just yet.

Come on Evolution, put that capability back in!!!

---

### Post by Slopwith on 2011-06-15
Pretty sure I could import directly with 10.04 a couple of months back but now after having to re-load so did with 10.10, no facility in Import Single file to select pst. You can browse for the PST file and select it but the import window does no acknowledge it as a viable format to import. What is happening?

---

