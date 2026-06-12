---
title: "doxymacs setup"
date: 2009-02-26
forum: General Help
---

### Post by pocketchange on 2009-02-26
I'm trying to use doxymacs with emacs.  I'm pretty new to emacs.  I'm having trouble with the README.Debian where I have to set the doxymacs-doxygen-root and doxymacs-doxygen-tags.  The part that's hanging me up is that as far as I know, doxygen is most useful when generating into a particular project folder.  Let's say:

~/Projects/prog1/docs/html
and 
~/Projects/prog2/docs/html

I'd like each project to put the files in it's own project docs folder.  I don't think that I want an absolute path.  I found something similar to what I want to do [here]("http://github.com/sigma/dotfiles/commit/e8f24cc2dec97ce90a1ade6e39b672a68b194f36").  Anyone have any suggestions?

By the way, the code on that page doesn't work.  It fails when I load emacs saying there's something wrong with the "request" line:

Symbol's function definition is void: request

---

