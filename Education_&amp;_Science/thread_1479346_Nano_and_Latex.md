---
title: "Nano and Latex"
date: 2010-05-10
forum: Education &amp; Science
---

### Post by Capta!nCrude on 2010-05-10
Hello!

I've recently decided that I want to learn how to construct articles with Latex. Under windows I have used Lyx, which I've found very good. However now I want to actually learn Latex, and for the documents I won't be using it, I'll turn to OpenOffice.org instead.

 There are however a few things I need help with;

[LIST=1]
[*]After creating a .tex file in nano, how do I convert it to .pdf and/or .dvi?
[*]Where can I find good Latex documentation, I've got "The not so short introduction to Latex"
[*]What packages must I install in order to get a good latex environment?
[/LIST]
Cheers!

---

### Post by AdotB on 2010-05-10
> **Capta!nCrude said:**
> [LIST=1]
[*]After creating a .tex file in nano, how do I convert it to .pdf and/or .dvi?
[*]Where can I find good Latex documentation, I've got "The not so short introduction to Latex"
[*]What packages must I install in order to get a good latex environment?
[/LIST]

Hi,
As for number 1: to compile the .tex file into dvi, use
```
latex doc.tex
```
to compile it into pdf use
```
pdflatex doc.tex
```
Also you might want to use some pdf-specific packages like this one:
```
\usepackage[pdftex,pdfauthor={your name},pdftitle={the title},pdfcreator={ },pdfproducer={ },bookmarks=true] {hyperref}
```

Number 2: there is some decent documention at ctan.org:
[http://www.ctan.org/tex-archive/info/](http://www.ctan.org/tex-archive/info/)
and also a wikibook: [http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX)

And for number 3:
To get latex up and running, you can install `texlive-latex-base' (about 180MB installed) or `texlive-latex-recommended' (about 350 MB installed). 
If you find that you need other packages, they can be installed as needed.

Also as for an editor, gedit has highlighting for latex, as does vim. I used to use kile which is a great full ide, but its for kde/qt. I generally use vim/gvim now.

Hope that helps.

---

### Post by Chronon on 2010-05-10
You can use any text editor you like to generate your LaTeX code.  This must be run through an interpreter to generate the actual document.  

In Ubuntu, you will want to install texlive.  This provides a working system with the necessary tools and main LaTeX packages.

[http://www.ctan.org/starter.html](http://www.ctan.org/starter.html)

---

### Post by Capta!nCrude on 2010-05-11
Thanks for the help, both of you. The links you provided seems to be exactly what I need to get started with latex.

/Capta!n

---

### Post by Azrael3000 on 2010-05-11
Hey Captain.

Well there's nothing wrong with what you are doing. However I wouldn't consider your way the most efficient (easiest).

I am currently writing my master thesis in latex using gedit with the latex plugin and it's a charm. You'll also find further threads here in this forum discussing the possible alternatives.

Best,
Arno

---

### Post by Capta!nCrude on 2010-05-11
Speaking about Gedit, I've been tinkering with it alongside with nano, and what I do like better is the different color syntax that Gedit has. Nano doesn't differ colors based on command which Gedit actually do. However, I haven't found any good dark color scheme for Gedit, that works well with the syntax coloring. Do you perhaps know one? I'm looking for something that's easy on the eyes.

Cheers!

---

### Post by Azrael3000 on 2010-05-11
did you try the ones that are predefined (edit->preferences->font & colors)? maybe cobalt?

Besides that I suggest some searching, it should be rather easy to insert a new color scheme you find online.

---

### Post by AdotB on 2010-05-14
I also like cobalt for gedit. Another theme i use a lot is zenburn.

[http://slinky.imukuppi.org/zenburnpage/](http://slinky.imukuppi.org/zenburnpage/)  (I think)

Here is my `zenburn_hc_gedit.xml' if anyone is interested. Its slightly modified from the one on the site to match the `high contrast' mode in zenburn.vim 
```
<?xml version="1.0" ?>
<style-scheme id="zenburn-hc" name="Zenburn - High Contrast" version="1.0">
	<author/>
	<_description>Zenburn theme</_description>
	<style foreground="#dcdccc" name="def:boolean"/>
	<style foreground="#7f9f7f" name="def:comment"/>
	<style bold="true" foreground="#dcdccc" name="def:constant"/>
	<style background="#8faf9f" bold="true" foreground="#ffffdd" name="cursor"/>
	<style background="#313c36" bold="true" foreground="#709080" name="diff:added-line"/>
	<style background="#333333" name="diff:changed-line"/>
	<style background="#464646" foreground="#333333" name="diff:removed-line"/>
	<style foreground="#efef8f" name="def:function"/>
	<style foreground="#efdcbc" name="def:identifier"/>
	<style bold="true" foreground="#f0dfaf" name="def:keyword"/>
	<style background="#3f3f3f" foreground="#858585" name="line-numbers"/>
	<style background="#1f1f1f" foreground="#dcdccc" name="text"/>
	<style foreground="#8cd0d3" name="def:number"/>
	<style bold="true" foreground="#ffcfaf" name="def:preprocessor"/>
	<style background="#385f38" foreground="#f8f893" name="search-match"/>
	<style foreground="#cfbfaf" name="def:specials"/>
	<style background="#3f3f3f" foreground="#e3ceab" name="def:statement"/>
	<style foreground="#cc9393" name="def:string"/>
	<style bold="true" foreground="#dfdfbf" name="def:type"/>
	<style background="#201010" bold="true" foreground="#ef9f9f" name="def:error"/>
	<style background="#332323" foreground="#e37170" name="def:error"/>
</style-scheme>

```
just save the xml file, go to Edit -> Preferences -> Fonts & Colors, and click `Add...'

---

### Post by Azrael3000 on 2010-05-15
looks nice, thanks. I'm gonna give it a try

---

### Post by myle on 2010-05-15
There is Kile which is excellent imho. No need for memorizing math symbols initially. Compiler and view process are a just a combination of two keys, spell checker, some simple wizards (or more accurately some bunches of usually used code) etc.

[http://kile.sourceforge.net/](http://kile.sourceforge.net/)

---

### Post by Capta!nCrude on 2010-05-16
@AdotB

Thanks for the Zenburn theme, it looks really nice. Will try it out more extensively and maybe make some changes of my own. Much appreciated!


@myle


I know about Kile, looks like an awesome application, as many of KDE's applications does. However I don't like to mix Gtk+ and Qt applications, not because of any technical reasons, just my blatant preferences. However doing mathematical stuff seems a lot more convenient in Kile and that is a big plus for Kile. Luckily I'm just a economics student, and don't need much mathematics in my essays.


Cheers!

---

### Post by kokoshmusun on 2010-05-16
I'm also learning LaTeX, I use TexMaker and I like it a lot.  Great and pretty GUI. I think it's worth trying.

---

### Post by hhlp on 2010-05-16
well this is my opinion :

 1.- lyx
 2.- texmacs
 3.- gedit with latex plug-ins
 4.- geany with latex plug-ins

---

### Post by Chronon on 2010-05-18
Lyx is not exactly LaTeX.  

I like Winefish pretty well too.

---

