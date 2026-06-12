---
title: "Emacs: rebinding key"
date: 2011-06-15
forum: Education &amp; Science
---

### Post by tekkenlord on 2011-06-15
Hello all,

I am trying to bind a key sequence that comments out a line in CC mode. The key sequence is "M-a C-SPC C-e M-;" which essentially goes to the beginning of the statement, marks, goes to the end of the line and comments out.

Since I rarely use the already defined keybinding "C-d" (which deletes forward a character), I thought to reassign it to my key-sequence.

I am using in my .emacs file:
(define-key global-map (kbd "C-d") (kbd "M-a C-SPC C-e M-;"))

Unfortunately, this works in the *scratch* buffer but not when editing .c files. In particular, pressing "C-d" deletes forward a character, which is the original action. Can anyone help me with this? Thanks.

---

### Post by gunksta on 2011-06-16
You are actually quite close to succeeding. What you have won't work because you are trying to define a macro in your define-key statement. You can't do that. For simple macros like this, it might actually be a nice feature but AFAIK, its not possible.

You need to [S]open emacs[/S] switch to your always open frame and define your command sequence as a macro, which is what it really is. Once you have created a macro, you need to name it and write to you inti.el file, so you can use it the next time emacs starts.

Rather than attempt to re-write what someone else who knows more than I has already explained, I give you links. Two useful links.

[http://www.emacswiki.org/emacs/KeyboardMacros](http://www.emacswiki.org/emacs/KeyboardMacros)

[http://www.emacswiki.org/emacs/CommentingCode](http://www.emacswiki.org/emacs/CommentingCode)

---

### Post by tekkenlord on 2011-06-17
Thank you very much. I followed the instructions in the first link, but unfortunately, the keybinding does not work when editing c files (it still works on the scratch buffer though).

I read carefully the CC manual and finally found out that the following will do the job:

(fset 'comment-current-line
   [home S-end ?\M-\;])

(defun my-c-initialization-hook ()
;; Assign C-d to comment in/out current line
(define-key c-mode-base-map (kbd "C-d") 'comment-current-line))
(add-hook 'c-initialization-hook 'my-c-initialization-hook)

The first part defines the macro and gives it a name. The second makes sure it is "seen" when writing in CC mode. 

Thanks again for all your help!

---

