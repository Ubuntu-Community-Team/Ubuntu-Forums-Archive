---
title: "Help with Lyx"
date: 2008-10-08
forum: Education &amp; Science
---

### Post by carlossosa on 2008-10-08
Dear all,

Every time that I try to open my thesis in Lyx I get the following error message: "The layout file requested by this document ***.layout is not usable. This is probably because a LaTex class or style file required by it is not available. Lyx will not be able to produce output"

I did everything mention in
[http://ubuntuforums.org/archive/index.php/t-440508.html](http://ubuntuforums.org/archive/index.php/t-440508.html)

and I am still getting same error.

I don't know what to do :( .

Carlos Sosa

---

### Post by GSBoomer on 2008-10-08
The .layout file is a LyX file and not a LaTeX file. In order for LyX to layout the document in a view, it has to have the .layout file. 

Take a look in /usr/share/lyx/layouts/. If the LyX layout file for your thesis style isn't there, you'll get that error.

---

### Post by carlossosa on 2008-10-09
I have copied the layout files into that directory and I still having the same problem. Do you have any other idea.

Thanks

Carlos Sosa

---

### Post by Deadredbeef on 2009-10-04
Hello guys,
Please help me.

I have to write a thesis and i want to use lyx.

I have installed lyx in kubuntu

There were no problems installing.

When i opened lyx and try to "open from template" and choose for instance IEEETran layout.

I get the following error:

```
  The layout file requested by this document,
 IEEEtran.layout,
 is not usable. This is probably because a LaTeX
 class or style file required by it is not
 available. See the Customization documentation
 for more information.
 LyX will not be able to produce output.


```There are alot of those templates.

How can i make those templates work?


Kind Regards

---

### Post by unutbu on 2009-10-04
Have you installed the texlive-publishers package?
I found the package by running ```
apt-cache search IEEETran
```. And according  to
```

apt-cache show texlive-publishers
```
it provides the "Document class for IEEE Transactions."

---

### Post by Khushboo_khan on 2009-10-08
Ooohhh i dont know what to do. i have a same problem please help me please

---

### Post by triyant on 2009-12-27
maybe it?

1) download ieetrans [here]("http://www.ctan.org/pub/tex-archive/macros/latex/contrib/IEEEtran.zip")
2) extract and get IEEEtrans.cls inside extracted folder
3) move it here :
```
sudo mv IEEEtran.cls /usr/share/texmf/tex/latex/
```
4) run texhash
```
sudo texhash
```
5) restart lyx ( reconfigure if needed )

---

### Post by jonobe on 2010-03-13
I tried the above: extracted fine, but couldn't run texhash, as the command was not found, so the problem is still there.

---

### Post by jonobe on 2010-03-14
This worked for me:


install (from your software manager/synaptic) 

 texlive-latex-extra-2007.dfsg.17-2ubuntu1(all)

(this is its current name)

which offers supplementary packages for lyx. 

Hope this helps.

---

### Post by dougvk on 2010-05-02
[http://www.rrfx.net/2009/06/howto-use-ieeetrancls-latex-class-file.html](http://www.rrfx.net/2009/06/howto-use-ieeetrancls-latex-class-file.html)

also, make sure to go to tools > reconfigure after installing everything.

---

### Post by lethalfang on 2010-05-05
Can't you just copy that layout file to the directory that you're working, i.e., the directory that contains your .lyx file?
That usually works or LaTeX, among many other things.

---

### Post by nardis_Miles1 on 2010-08-13
I am also having problems with lyx in lucid. In my case, it is with revtex4.layout. I have checked that this file is in /usr/share/lyx/layouts.
I have also made sure that a file revtex4.cls is in 
/usr/share/texmf-texlive/tex/latex/revtex/ and I have created a symbolic link to that file in /usr/share/texmf/tex/latex/lyx. I should point out that this setup continues to work on my karmic laptop. In fact, this is one of only a few reasons that I'm keeping karmic on my laptop. =P~

If anyone has had success with lucid and some of the special layouts, please tell me how I'm being stupid (this time).

---

### Post by mkupsta on 2010-11-18
> **dougvk said:**
> [http://www.rrfx.net/2009/06/howto-use-ieeetrancls-latex-class-file.html](http://www.rrfx.net/2009/06/howto-use-ieeetrancls-latex-class-file.html)

also, make sure to go to tools > reconfigure after installing everything.

Thank you, this worked on 10.10.

---

### Post by samuel.toma on 2011-02-16
perfect !!! every thing works fine now !!! thx so much :D:D:D:popcorn:

---

### Post by denilw on 2011-03-30
I had this error after install two versions of lyx.  This solution worked for me. Thanks.

---

### Post by suryaworldedu on 2011-04-01
i also had the same problem. Thanks for helping me out.

---

