---
title: "ZIM desktop and space"
date: 2011-01-25
forum: Desktop Environments
---

### Post by RikoW on 2011-01-25
Dear all,

I like the zim desktop wiki for notes taking ... in principle. The thing that makes it essentially useless for me is that hitting the space bar which not insert a space but switch to the outline pane on the left.
SHIFT+space creates a regular space. Why is that???

Is there a way to change that? I tried the Preferences already but without success.

Any hint would be appreciated.

Thanks,
        Riko

---

### Post by gmargo on 2011-01-25
Sounded interesting, so I installed zim and gave it a try.  Spaces act as expected for me - as normal text.  Alt-Space switches to the side panel.

I don't know how your zim got into such a state, but you might check the configuration files under **$HOME/.config/zim/**, especially "accelmap".

---

### Post by RikoW on 2011-01-25
I found a/the (?) solution. Didn't seem to have anything to do with zim itself but rather with the keyboard layout. 

I noticed, that in the layout the space bar was not just space but labeled ISO_next_group. I don't really know what that means, but it sounded like it could cause a problem. So I played with the options in the keyboard layout dialog and there changed the *using space key to insert non-breakable space charactar* from *default* to *usual space at any level*.

Now zim behaves as expected and so far I didn't observer any differences in the space-bar usage anywhere else.

Maybe that will be helpful for someone else, too.

Cheers,

           Riko

---

