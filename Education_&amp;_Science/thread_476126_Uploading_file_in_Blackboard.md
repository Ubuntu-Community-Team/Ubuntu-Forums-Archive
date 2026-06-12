---
title: "Uploading file in Blackboard"
date: 2007-06-16
forum: Education &amp; Science
---

### Post by peter_k on 2007-06-16
Got one here that is simply driving me crazy:

My wife is taking a class online, and they use the Blackboard system for submitting their files for assignments.  She types her assignment on my Ubuntu box (in Open Office 2.2), and she saves it as a Word .doc.  After she hits "browse..." to upload her file, she clicks Submit, where she hereby gets the "Please enter a real filename" dialog box.  Any idea why this would be happening?  I don't believe it is a Linux issue, necessarily, as we were able to get to the page (I'm using Feisty, and Firefox 2.0.0.4).  It may perhaps be the filename...as it's a UNIX box, there is no "C:" drive in the filename of course...I believe the filename was /home/aileen/WA1ACarroll.doc.  Is it because Blackboard doesn't recognize a file starting with "/home..." as a valid path?  I also tried just entering the filename itself (WA1ACarroll.doc), but with the same result.  Has anyone dealt with this before?

---

### Post by DrOlaf on 2007-06-18
I use Blackboard a lot (as an instructor, not a student, I should say) with Ubuntu and I haven't had the problems you describe. I can upload .doc files, or zipped webpages, without a problem. Do you only see this problem when you access Blackboard via Ubuntu - have you tried the same thing from Windows?

---

### Post by peter_k on 2007-06-18
> **DrOlaf said:**
> I use Blackboard a lot (as an instructor, not a student, I should say) with Ubuntu and I haven't had the problems you describe. I can upload .doc files, or zipped webpages, without a problem. Do you only see this problem when you access Blackboard via Ubuntu - have you tried the same thing from Windows?

Dr. Olaf:

Thanks for the reply!

Yes, my wife tried it on a Windows PC, and it works just fine with Windows.  I don't think it's a "Ubuntu thing" really, as I can access the page.  I think it's more an issue with the filename when attaching.  When you attach files, do you normally just supply the filename (i.e. foo.doc), or the whole path (i.e. C:/My Computer/My Documents/foo.doc)?  Have you ever attached a file off of a network with Blackboard?  If so, how do you handle the filepath?  I think the /home/...  might be what's messing it up, as Blackboard doesn't see a valid path.  I've tried entering just the filename, and that didn't work either.  Unfortunately, my wife is the one who did it in Windows, so I didn't see the path, but she tells me that it started with a C:/, so I'm guessing she specified the entire path as opposed to just the filename.

When I looked for help files for Blackboard, as well as with a Google search, the only thing I could see regarding filenames was the standard "no spaces, no special characters except the underscore", and a size limit of 32 characters with the extension included.  No info regarding networks, or Unix style filepaths.

---

### Post by DrOlaf on 2007-06-18
When I attach a file, I hit the 'browse' button and then click my way through the folders to find the file that I want, and then I click on 'Submit' to upload the file. I don't type in the path name manually.

It works fine with files that are on my local hard drive (like /home/olaf/teaching/courseweb/thisweekslecture.zip), and also with files on a flash drive (like /media/flashdrive/documents/teaching/thisweekslecture.zip). I haven't tried uploading from a network share, but I'll try that and see how it goes. I've just logged on to my Blackboard server, and it's running v6.1.374 of the software, but I doubt that's your problem. I've uploaded files from my Ubunutu PC, from my Windows PC (it's the same machine, but it dual-boots) and from my Mac, and Blackboard can cope with the different path formats.

I have to say I find Blackboard's help files incredibly unhelpful.

---

### Post by peter_k on 2007-06-18
Hmmm.  Sounds like I'm doing exactly what you are, but it's not working.  I'll have to try it again, and see if there's anything peculiar about my setup that I didn't notice before.  Thanks, because at least this tells me it's not a path issue, so that's one variable down.  :)

Ditto on the cruddy help files.  I had been told about this before, so I just went with a Google search, bypassing their help altogether.

---

### Post by Modred on 2007-06-18
It is possible (at least, I'm fairly sure it's possible) that the Blackboard admin at the school she's using have put in some sort of custom script that checks the filename and only recognizes Windows-style paths.  You might try contacting the admin at the school to see if that's the case.  Even if it's not, he or she might be better suited to help you.

---

### Post by peter_k on 2007-06-18
> **Modred said:**
> It is possible (at least, I'm fairly sure it's possible) that the Blackboard admin at the school she's using have put in some sort of custom script that checks the filename and only recognizes Windows-style paths.  You might try contacting the admin at the school to see if that's the case.  Even if it's not, he or she might be better suited to help you.

Good point, Mordred - I'll check into that as well.

---

### Post by akniss on 2007-06-18
Have you tried using a different browser?  Maybe epiphany or opera?  Another option is to try the user agent switcher extension for firefox.  I often use firefox with WebCT (which I think is a close relative to Blackboard), and although I don't have issues uploading files, technically Firefox is not a supported browser.  The user agent switcher allows firefox to 'appear' as IE, Netscape, or Opera to web servers.  I use it often to access pages that are "IE only" sites.

---

### Post by peter_k on 2007-06-19
> **akniss said:**
> Have you tried using a different browser?  Maybe epiphany or opera?  Another option is to try the user agent switcher extension for firefox.  I often use firefox with WebCT (which I think is a close relative to Blackboard), and although I don't have issues uploading files, technically Firefox is not a supported browser.  The user agent switcher allows firefox to 'appear' as IE, Netscape, or Opera to web servers.  I use it often to access pages that are "IE only" sites.

Good point, and a good tip, as I may need to use that at some point in the future, if I never need to access an IE only site.  

BTW, as a former web designer, however, I would say that any site that sets up itself as "IE only" is making a mistake, as users will definitely be shut out.  Granted, I know they exist, but to me it just seems like a bad programming practice.  I do remember what a pain it was to code for both IE and Netscape back in the day, but it was always considered essential, as otherwise the help desk would get inundated with "this doesn't work in Netscape" tickets, which they would promptly pass to us, so we had to deal with it anyway.  With Firefox, Safari, Opera, and the multitude of other browsers out there, it's probably even more of a pain today, but still good practice to be as platform-neutral as you can.  Off the soapbox now, I promise. :)

In the case of Blackboard, however, Firefox is definitely supported.  In fact, somewhere in their documentation, I saw where Blackboard talks about a bug in IE, and advises users that the best way to get around the bug is to use Firefox instead. :o

---

### Post by Modred on 2007-06-19
> **peter_k said:**
> In the case of Blackboard, however, Firefox is definitely supported.  In fact, somewhere in their documentation, I saw where Blackboard talks about a bug in IE, and advises users that the best way to get around the bug is to use Firefox instead. :o

Yeah, their "fancy" (annoying) text editor has caused IE7 to freeze up and crash.  My university actually recommended people not upgrade to IE7 because of the flaw!  But I'm guessing the problem will be fixed in the next round of updates.  Of course, that still doesn't explain why you're having problems...

---

### Post by Reb on 2007-06-20
Just throwing my 2 cents in, but I've never had a problem with blackboard (other than the fact it's a horrible piece of software).

---

### Post by jmfrey on 2007-07-31
Just so you don't feel alone.  I too am having this problem.  I am running Debian Lenny (amd64).  I wouldn't be at all surprised it is related to the firefox (iceweasel on Debian) in 64-bit since a lot of things have had problems.

Are you running a 64-bit system?

---

### Post by jmfrey on 2007-08-02
I found a solution that appears to have worked for me in getting past the error and submitting the assignment.

By escaping the slashes, I was able to get the server to accept my file.

Where...

```
/home/user/document.doc
```

failed,
```

\/home\/user\/document.doc
```

worked.

---

### Post by WedgeHG on 2007-10-26
I had the same problem that you describe. Here is the problem in my case:

There is client-side validation that checks to make sure that the path to the file that you gave it is valid. It looks like this:

```
function FilePickerValidator_check()
  {
    if ( this.CSFile.exists() && !this.LocalFile.isEmpty() &&
         !this.CSFile.isEmpty() )
    {
      alert( "Two files have been entered. Only one file can be attached.  Use Add Another File to attach multiple files." );
      return false;
    }
    else {
    	// Mac do not have option to type the file name, so no need to check the path
    	if( navigator.userAgent.toLowerCase().indexOf( "mac" ) >-1 )
    		return true;

    	if(this.LocalFile.exists() &&  !this.LocalFile.isEmpty() && !(this.LocalFile.value().indexOf("\\") ==0 || this.LocalFile.value().indexOf(":\\") !=-1) ){
    		alert("Please enter a valid file." );
    		//document.getElementsByName(this.LocalFile.name())[0].focus();
    		var tmp = this.LocalFile.name;
        var tmp2 = document.getElementsByName(tmp)[0];
        tmp2.focus();
    		return false;
    	}
    return true;
	}
  }
```

Basically what this is doing is saying "Are you a Mac?"

If the answer is "Yes" then it says "fine, Macs don't let you manually type a path so whatever you have must be fine. Approved."

If the answer is "No" then it must assume that you are a Windows machine and checks to see if your path conforms to Windows norms. A path like "/home/wedge/mydoc.doc" looks to be invalid so it refuses to take it. 

The key to the workaround that I found is that it doesn't even check the path if it thinks you are a Mac. To detirmine if you are a Mac it just checks for the presense of the string "mac" (not case sensitive) in the user agent string that your browser sends. So you can get a user agent switcher (available [[COLOR="Blue"]here[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/59") for Firefox, should be just a couple clicks to get it installed). Now just create a new user agent and just put the word "mac" on the line for user agent.  Then when you go to upload your file just switch to that custom one and it will think you are a mac and accept your file.

---

### Post by ScottKidder on 2008-01-07
Just found this, thanks for the workaround!

---

### Post by jonno on 2008-05-26
Thanks WedgeHQ! My wife is an online teacher at the local community college and she had the same problems. Guess I should try to get them to add all unix-based systems to behave like the mac.

---

