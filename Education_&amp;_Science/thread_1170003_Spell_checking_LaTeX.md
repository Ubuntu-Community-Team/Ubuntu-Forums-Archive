---
title: "Spell checking LaTeX"
date: 2009-05-25
forum: Education &amp; Science
---

### Post by samden on 2009-05-25
SOLVED

I am doing the final spell-check on my thesis (in LaTeX) before handing it in, but am finding it difficult to check it in British english - everything defaults to US english.

I am using aspell, with the command
```
aspell --lang=en_GB -c document.tex
```

However this says that the words "faeces" and "practice" are incorrect, while they are clearly correctly spelled according to the Oxford dictionary.

This is concerning as it means the word "feces" for example must be entered in the British english dictionary, yet I would want to change it to "faeces". Adding "faeces" to the dictionary won't change the fact that aspell probably won't pick up the American spelling "feces" if I have written it anywhere. It could well be missing other words I don't realise.

Does anyone have any good ideas for how to spell-check a document while 
- ignoring LaTeX coding 
- removing all words in US spelling?

---

### Post by meho_r on 2009-05-25
Have you tried with GUI editors like Kile or Texmaker? Last Texmaker even has inline spellchecker and it does skip codes. 

Do you use babel with "british" for British english?

In Kile, you can select text, run spellchecker and choose a dictionary (british). However, Kile doesn't skip LaTeX code :(

In Texmaker, you may choose spelling dictionary in Options > Configure Texmaker > Editor. Dictionaries are usually located in /usr/share/myspell/dicts

I hope this will help.

---

### Post by samden on 2009-05-25
I am using Gedit, but the inbuilt spellchecker doesn't recognise LaTeX code. 

I would love a stand-alone spellchecker I could just feed all my files through, rather than fussing around with the GUI spellchecker in Gedit. I'll muddle along somehow without one of course, but I just thought there might be a standalone tool already available.

I have not been using babel, what does it do and how would that help? I thought it just dealt with hyphenation, special characters and that sort of thing.

---

### Post by meho_r on 2009-05-25
I'm not sure about stand-alone spellchecker, but I think you should give Texmaker 1.9 a try since it does recognize LaTeX code and skips it while doing a spellcheck.

As for babel, it's a multilingual package for use with LaTeX. It takes care of all language specific tasks, sectioning, TOC, hyphenations etc. I don't know how deep differences between american and british english go, but just to be sure, I would use babel with "british" or "UKbritish" options. Check babel documentation for more infos.

I would recommend you to visit [LaTeX Community Forum]("http://www.latex-community.org/forum/") where you can get more thorough explanations and advices in this regard ;)

---

### Post by samden on 2009-05-25
Thanks for the help. 

Rather than install Texmaker and get into clunky GUI stuff I've kept using aspell, it works very well. I was frustrated with particular words, but I think that is just an issue with the default dictionaries used by aspell and I am unlikely to find any improvement with other software - they mostly seem to use the aspell dictionaries anyway.

Having just solved the problem myself and got used to the tools I probably shouldn't have bothered starting this thread, I'll mark it solved now.

I'd recommend aspell to anyone else in my situation.

EDIT: Well, I would mark it solved if I could figure out how to!

---

### Post by leorolla on 2009-11-24
To ignore latex code and specially the *labels*, how did you do?

---

### Post by samden on 2009-11-24
<removed by author>

---

### Post by mali2297 on 2009-11-24
> **leorolla said:**
> To ignore latex code and specially the *labels*, how did you do?

Use the *tex mode*,
```

aspell check --mode=tex document.tex

```

---

### Post by leorolla on 2009-11-25
Thank you!

I also found the solution in aspell manual and here:

[http://ubuntuforums.org/showthread.php?t=1259557](http://ubuntuforums.org/showthread.php?t=1259557)

---

