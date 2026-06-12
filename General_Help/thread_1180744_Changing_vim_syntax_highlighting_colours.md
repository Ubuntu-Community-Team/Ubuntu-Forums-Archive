---
title: "Changing vim syntax highlighting colours"
date: 2009-06-07
forum: General Help
---

### Post by infernus_crusher on 2009-06-07
I'm not sure which file to modify if I want to change vim's default syntax highlighting colour sets. The default colour set does not rhyme well with my black background terminal.

---

### Post by adrianx on 2009-06-07
[B]Edit (Again):

[/B]I have vim-full installed and the colour schemes are in:

/usr/share/vim/vim72/colors/

I see that "desert" is one of them. Please disregard what I've said below (except maybe the .vimrc thing).

------------------------------------
This worked for me:

[http://www.vim.org/scripts/script.php?script_id=105](http://www.vim.org/scripts/script.php?script_id=105)

Afterwards, I put ":colorscheme desert" (without the quotes) in ~/.vimrc

**Edit:** It's still not perfect, but maybe there are some other schemes that work better.

---

### Post by infernus_crusher on 2009-06-27
Many thanks, but I forgot to mention that the problem lies in vim not able to recognise different syntax highlighting colours depending on the file extensions. So if I have a file called Test.java, the following program

public class Test
{
public static void main()
{

}
}

will come out as white text on black background and nothing more than that. I tried :colorscheme darkblue, :colorscheme blue, etc and although it does change the defualt text and background colours, it does not seem to highlight any particular syntaxes.

Is there any way to fix this?

---

### Post by sdennie on 2009-06-27
Do you have syntax highlighting turned on?  Try typing ":syntax on".

---

### Post by Simian Man on 2009-06-27
Yeah, :syntax on is most likely going to fix your problem.  You can also find many color schemes [here]("http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/index-c.html").  Just save the .vim files to ~/.vim/colors.

---

### Post by adrianx on 2009-06-27
> **infernus_crusher said:**
> Many thanks, but I forgot to mention that the problem lies in vim not able to recognise different syntax highlighting colours depending on the file extensions. So if I have a file called Test.java, the following program

public class Test
{
public static void main()
{

}
}

will come out as white text on black background and nothing more than that. I tried :colorscheme darkblue, :colorscheme blue, etc and although it does change the defualt text and background colours, it does not seem to highlight any particular syntaxes.

Is there any way to fix this?
Are you sure you have **vim-full** installed? (Not that  funny default version of vi that spews out ^B^V.... when you use the arrow keys) :D

---

### Post by infernus_crusher on 2009-06-27
Ah yes, :syntax on did solve my problem.

Now the remaining problem is to make all these default. For now I still need to type ":syntax on" and ":colorscheme: desert" each time I load up vim. Which file do I need to change to make them default?

---

### Post by Ayuthia on 2009-06-27
You should be able to add them to the .vimrc file.  Just leave out the : if I recall correctly.

---

### Post by infernus_crusher on 2009-06-27
Brilliant. Thanks everybody.

---

