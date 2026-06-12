---
title: "Karmic shows Infinity Symbols µ"
date: 2009-11-13
forum: Desktop Environments
---

### Post by Darktrax on 2009-11-13
All kinds of PDF document viewers display the "µ" character as something looking very like the math "infinity" symbol. Disconcerting, since I need to look at many electronic data sheets that use it lots (eg. µV,
µV/°C ).

The desktop is Gnome, and the default viewer is "Evince 2.28.2" which, states "Using poppler 0.12.0 (cairo)" in its "About" box.

I also tried "xpdf" - kinda retro, but it does the same.

So does Okular, which is a very KDE application - same behaviour

So, maybe its something more fundamental about fonts, I don't know. I would be grateful for any suggestions..
G

---

### Post by coffeecat on 2009-11-13
I've just tried an admittedly not very scientific experiment. I copied and pasted the text of your post into OpenOffice Writer, changed the font to Arial (simply to get a clearer look than the default Times New Roman that OO gave me) and then File > Exported to PDF. Then I opened the PDF in Evince, Adobe Acroread and Okular, and the µ symbol looks fine to me - that's in Karmic. Well - not quite fine in Okular. The whole page rendering in Okular was inferior to what I remember of the Jaunty version, but that's something I'll look into separately.

I'm afraid I know the square root of very little about fonts in PDFs, just that you have embedded and non-embedded. :? But it seems that the µ symbol doesn't always look like an infinity symbol in Karmic.

Suggest:

Post a screenshot so that we can see.

Can you attach a small pdf file to your post (Manage Attachments button when you post)? I don't know the size limit but you can attach a pdf.

Failing that, how about a link to a viewable PDF so that others can check this out in their viewers?

Lastly - do you want to try Acroread? You have to enable the Partners Repository to get that. Open Synaptic > Settings > Repositories > Other Software Tab. Tick the archive.canonical line, and do a reload.

---

### Post by Darktrax on 2009-11-15
> **coffeecat said:**
> 
Post a screenshot so that we can see.

Hi coffeecat. Thanks for the reply. I did try, but it didn't work. I have a PNG of the top corner of the document, that came out at 27K. Maybe thats too much for the forum.

BUT - I have made progress!  :)

This is all because of the font in the document, or some feature of the document, and not something wrong with the PDF viewers. When I try the very same PDF viewers on other (maybe more modern!) documents that also use that character, it seems they are quite capable of displaying the "µ" symbol - meaning "micro".

Clearly the ASCII code used for that character, as embedded in the document, is wronly taken to deliver a "µ". Now that I have magnified it (when getting the screenshot), its not quite the complete "infinity" character - like a figure 8 laying on its side. Instead, its maybe the "proportional" character where the loop is not completed.

Now that I know that this is just a feature of some old documents, and not a pervasive problem with the PDF applications, I am reassured.

---

### Post by Dullstar on 2009-11-15
Would you post a screenshot?

---

### Post by pwaltman_1972 on 2009-11-23
> **Dullstar said:**
> Would you post a screenshot?

BUMP

I'm getting the same behavior, and have attached both a screenshot as well as the original file.

The character that is being displayed is definitely the 'proportional to' character, though, it dispalys correctly in xpdf.

I compared the behavior of evince on another machine running Karmic (though it's a 64-bit machine) and evince displayed it correctly there as well.

I've gone through the fonts packages (searched for 'font' in the synaptic package manager) for both machines and while they're nearly the same, they're not exactly.  I fixed most of the differences and Evince is still not displaying the character correctly.  The only differences I didn't fix is that texlive is installed on the machine that's not displaying the 'mu' char correctly, but isn't installed on the machine that does display it correctly.

---

### Post by mikl-dk on 2010-04-19
Any news on this? I have the same problem on 10.04.

---

### Post by Ceiber Boy on 2010-04-19
> **pwaltman_1972 said:**
> BUMP

I'm getting the same behavior, and have attached both a screenshot as well as the original file.

The character that is being displayed is definitely the 'proportional to' character, though, it dispalys correctly in xpdf.

I compared the behavior of evince on another machine running Karmic (though it's a 64-bit machine) and evince displayed it correctly there as well.

I've gone through the fonts packages (searched for 'font' in the synaptic package manager) for both machines and while they're nearly the same, they're not exactly.  I fixed most of the differences and Evince is still not displaying the character correctly.  The only differences I didn't fix is that texlive is installed on the machine that's not displaying the 'mu' char correctly, but isn't installed on the machine that does display it correctly.


I'm running Ubuntu 9.10, Karmic 64-bit and it all displays correctly for me in my document viewer, being an engineer myself i can appreciate how frustration it is when symbols are not correctly displayed. It might be a good idea to use Acroread as someone else has previously suggested, even if its just out of interest rather than scientific endeavor!

Good luck

---

### Post by mikl-dk on 2010-04-19
> **Ceiber Boy said:**
> I'm running Ubuntu 9.10, Karmic 64-bit and it all displays correctly for me in my document viewer, being an engineer myself i can appreciate how frustration it is when symbols are not correctly displayed. It might be a good idea to use Acroread as someone else has previously suggested, even if its just out of interest rather than scientific endeavor!

Good luck

acroread shows mu just fine, but to me it's a temporary solution rather than a permanent one. But thanks :-).

---

### Post by ejchica on 2010-06-04
Hi I also have this problem now. Any new development on this?

If it helps something, I did not have this problem in karmic, I got only after upgrade to lucid. Evince and Okular show wrong symbols, Xpdf and Acroread are fine. 

Also, It is not only the mu symbol but also the degree symbol (changed to something resembling a a gamma), likely other symbols are also affected, alpha and beta are shown ok. 

I wonder whether it is an R related issue, I just created a pdf in writer with the mu and degree symbols and were shown good. I will be posting in a R forum too.

---

### Post by andricas on 2010-06-10
I have been having the same problem with okular (but not xpdf) since switching to ubuntu 10.04: some greek characters are often replaced by some other symbol in pdf, ps and dvi files. This does not happen for equations but it seems to always happen for labels in figures generated by mathematica and matlab.

---

### Post by rahaydenuk on 2010-08-25
Hi I also have the same problem on 10.04. For example, $\mu$ shows as "proportional to" and $\pi$ as $\neq$.

I'm shocked this has been an issue in some form for almost a year and yet nothing has been done. This is really quite serious for anyone who does any work with mathematical documents. I hate Acrobat and really don't want to use anything other than evince, which I've been using fine for years.

Please fix this someone!

Richard.

---

### Post by lave on 2010-08-30
I also had this problem, a pdf-file (probably generated in Windows-Word) shows wrong symbols for \mu, \Omega etc. To solve this I removed a package named ttf-symbol-replacement and it now works as expected. I also has a package called ttf-symbol-replacement1.3 (probably from the wine ppa) and if I install that it also works.

Good luck

---

### Post by coffeecat on 2010-08-30
> **rahaydenuk said:**
> Please fix this someone!

Who is this addressed to? Very few developers frequent these forums. Forum members are mostly ordinary users. If you are really that shocked I suggest you look on Launchpad to see if there is a bug report posted. Contribute to the thread if there is one, or start one if not. Developers need to be made aware of bugs they do not know about. Launchpad is the way to do that.

---

### Post by lkilcher on 2010-11-05
> **lave said:**
> I also had this problem, a pdf-file (probably generated in Windows-Word) shows wrong symbols for \mu, \Omega etc. To solve this I removed a package named ttf-symbol-replacement and it now works as expected. I also has a package called ttf-symbol-replacement1.3 (probably from the wine ppa) and if I install that it also works.

Good luck

Bump.

Removing ttf-symbol-replacement worked for me as well.  I couldn't find the ttf-symbol-replacement1.3 package in my set of repositories, but didn't bother looking because removing the first worked.  I was getting this problem when viewing pdf figures in evince.  The figures had been generated in Matlab and the characters I was having issues with were \circ and \Delta.

thanks!

---

### Post by atentik on 2011-05-07
This does not seem to solve the problem with okular. I removed the ttf.... file but the problem persists.

---

