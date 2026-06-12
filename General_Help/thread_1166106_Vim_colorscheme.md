---
title: "Vim colorscheme"
date: 2009-05-21
forum: General Help
---

### Post by m_ad on 2009-05-21
I know this issue has been brought up a lot, but my question is a little different. Anytime I try and apply a colorscheme that I obtained from vim.org, vim spits out errors.

At first, I thought it was just the colorscheme I tried to apply. After trying to apply 10-15 colorschemes with no success (all error messages), I thought I was doing something wrong.

For example, [eclipse.vim]("http://axisym3.net/jdany/wp-content/vim/eclipse.vim") gives the following errors

```
[matt@ubuntu-laptop]:[~]$ vim .vimrc
Error detected while processing /home/matt/.vim/colors/eclipse.vim:
line    6:
E474: Invalid argument: background=light^M
line    7:
E411: highlight group not found: clear^M
line    8:
E15: Invalid expression: exists("syntax_on")^M
line   93:
E171: Missing :endif
Press ENTER or type command to continue
```

Similar errors occur for any other colorscheme I've tried to apply.

EDIT: Ahh, what are the ^M's? I downloaded the file and cp'd it directly to ~/.vim/colors and added 'colorscheme eclipse' to vimrc.

---

### Post by Claus7 on 2009-05-21
Hello,

just a quick one: the ^M are part of a document that usually appear if you transfer it from msdos/windows to a linux box. Sometimes they put impediments and sometimes not. The best thing you can do is to erase them manually. I do not think that you can rid off them otherway. 

If the file sais that it misses an endif, that means that either the code is wrong or it cannot understand it because of the presence of these ^M's. Erase them and see what you will get.

Regards!

---

### Post by geirha on 2009-05-21
DOS uses '\r\n' as line-endings, while linux uses just '\n'. The '\r' will commonly appear as ^M in linux. You can use the sed command to get rid of them.
```
sed -i 's/\r$//' /home/matt/.vim/colors/eclipse.vim
```

---

### Post by m_ad on 2009-05-21
> **Claus7 said:**
> Hello,

just a quick one: the ^M are part of a document that usually appear if you transfer it from msdos/windows to a linux box. Sometimes they put impediments and sometimes not. The best thing you can do is to erase them manually. I do not think that you can rid off them otherway. 

If the file sais that it misses an endif, that means that either the code is wrong or it cannot understand it because of the presence of these ^M's. Erase them and see what you will get.

Regards!

Thanks for the help. I can't see any ^M's explicitly in the file.

> **geirha said:**
> DOS uses '\r\n' as line-endings, while linux uses just '\n'. The '\r' will commonly appear as ^M in linux. You can use the sed command to get rid of them.
```
sed -i 's/\r$//' /home/matt/.vim/colors/eclipse.vim
```

Thanks, I'll try this. Are the M's put in there because I saved the file using Firefox?

EDIT: That worked, thanks geirha. what is the sed command doing?

---

### Post by geirha on 2009-05-21
> **m_ad said:**
> Thanks for the help. I can't see any ^M's explicitly in the file.
 When a file has DOS-endings, vim opens it in dos mode, and new lines you add will be saved as '\r\n'.
```
:set fileformat=unix
```
will switch to unix mode and you'll see the '\r's as ^M

EDIT: No actually, it won't display the '\r's, but if you save it after changing fileformat, the '\r's will be removed too.

> **m_ad said:**
> 
Thanks, I'll try this. Are the M's put in there because I saved the file using Firefox?

EDIT: That worked, thanks geirha. what is the sed command doing?

The ^Ms are there because whoever wrote it, wrote it in a DOS/Windows editor.

The syntax for the sed substitution is "s/<pattern>/<replacement/"
So it searches for pattern "\r$" which means \r at the end of the line ($ matches end of line), and replaces it with an empty string.

---

### Post by m_ad on 2009-05-21
Thanks for the help. I'll have to read up on the DOS/Unix formats :)

---

