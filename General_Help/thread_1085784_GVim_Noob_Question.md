---
title: "GVim Noob Question"
date: 2009-03-03
forum: General Help
---

### Post by BJ_Covert_Action on 2009-03-03
So I know this isn't necessarily a general Linux help forum, or  a Vim forum for that matter, but I figure someone here should be able to help me with this fairly quickly. 

I've been trying to learn vim lately and as a "training wheels" exercise have been primarily using the GUI version, GVim. One of the things I wanted to do was change my tab width option so, like a good little GUI user I went into the Edit Menu, to the settings window. To my delight, in a split window a whole settings file popped up where (I assumed) I could change all the options my little heart desired. Well I paged down and found the tab width settings and changed them appropriately. However, when I typed :w to save my new settings I got an error that read something along the lines of:

"Cannot Write, 'buftype' option is set"

So I did some scrounging, found the 'buftypes' option was equal to nothing, blank, "", whatever you want to call it. I didn't change this because I honestly did not know what all it did.

I did find, however, that I could mod my tab settings in my _vimrc file (this is a windows box I am on now *blech*) and did so and it worked fine.

However, now I am curious. If you can't save the settings file that is accessed via the edit menu, what is it? Is it just there for reference? Is there a way to save it by modding the buftype parameter, and do you have to change that parameter every time? I guess in general, what is the point of the settings window on the edit menu in GVim? Is it reference? or is it someplace you are actually supposed to mod your settings?

Thanks in Advance Guys,
Brady

P.S. I did try to do some Google searching (albeit scant) and did not find a lot of info that didn't involve editing the vimrc file.

---

