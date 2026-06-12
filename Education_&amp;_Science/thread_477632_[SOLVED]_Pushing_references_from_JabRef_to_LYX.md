---
title: "[SOLVED] Pushing references from JabRef to LYX"
date: 2007-06-18
forum: Education &amp; Science
---

### Post by dysonsphere23 on 2007-06-18
Hi,

I have searched the forum and can't find anyone posting this problem.  Sorry if it has been covered.

I am just getting started with using LYX to write scientific papers.  I am coming from an EndNote/Word background but like the idea of TeX and open source in general.

I have downloaded JabRef to replace EndNote and it has a function that should "Push selection into LYX".  However when i push this button, or select from the dropdown menu, nothing happens.

I am able to generate a bibtex bibliography in LYX with Insert>List/ToC>Bibtex bibliography.  I find that this is a good function, however it would be great if I could exploit all the features of JabRef.

Can anyone offer some advice, perhaps there is a configuration in JabRef or Lyx that I am missing?

Thanks in advance.

---

### Post by kleeman on 2007-06-18
Do you get an error message in the bottom jabref bar? Someimes the problem is that jabref and lyx do not agree where the file is to transfer info between them. Typically jabref assume it is in $HOME/.lyx/lyxpipe ($HOME is your home directory)

In lyx you set it in 

Tools-----> Preferences----> Paths----> Lyxserver Pipe

You need to reconfigure lyx for this to take effect and then restart lyx

---

### Post by dysonsphere23 on 2007-06-18
Wow, thanks that worked like a charm.

---

### Post by dannemil on 2007-07-09
Why not simply use the Insert ---> Citation in Lyx. Once you have told Lyx what the Bibliography file is, you should be able to do an Insert --> Citation (from menus) and find any of the references that you have in your bibliography reference file. Lyx will insert a link to the selected reference at that point in the text. You don't need to have JabRef open to do this.

---

### Post by sputnik on 2010-01-13
> **dannemil said:**
> Why not simply use the Insert ---> Citation in Lyx. Once you have told Lyx what the Bibliography file is, you should be able to do an Insert --> Citation (from menus) and find any of the references that you have in your bibliography reference file. Lyx will insert a link to the selected reference at that point in the text. You don't need to have JabRef open to do this.

It depends how you use software like Jabref.  I have a very large databases which is more searchable in jabref - I might want to check the abstract, or review, or keywords to make sure I have the right reference (or come to that all the references I want to cite on a particular point), and then push it/them to Lyx.

---

### Post by tintas on 2012-05-22
> **kleeman said:**
> Do you get an error message in the bottom jabref bar? Someimes the problem is that jabref and lyx do not agree where the file is to transfer info between them. Typically jabref assume it is in $HOME/.lyx/lyxpipe ($HOME is your home directory)

In lyx you set it in 

Tools-----> Preferences----> Paths----> Lyxserver Pipe

You need to reconfigure lyx for this to take effect and then restart lyx

Hello 

I am actually facing the same error msg in jabref. i went to lyx to the following path but then under lyxserver pipe, there was nothing and i had to browse the path, and here i didnt know how to proceed.

another problem i also saved the the jabref file in the same folder as my lyx file, and tried to insert citation in lyx. i was told that lyx should automatically recognize the citations but apparently the citation window is empty
i am really finding hard time with he bibtex citations and bibliography...
can anyone assist
thx
Tania

---

### Post by overdrank on 2012-05-22
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

