---
title: "Licensing issue"
date: 2009-02-11
forum: General Help
---

### Post by cb951303 on 2009-02-11
I was looking for flash based movie player to embed to a commercial site of mine.

Fortunately I found this: [http://flowplayer.org](http://flowplayer.org)
It's open source. GPL licensed to be exact. Along with GPL licensing it offers a commercial license. According to website, the commercial license gives to client, the right to remove "Flowplayer" logo and replace it with their brand. So far so good. The thing I don't understand is this: According to GPL, you can take the source code, modify it and then sell it, if you make the modified source code public. But according to flowplayer team, you can't remove their logo, if you're using it for free.

I know a product can be licensed as GPL and commercial at the same time, but doesn't the commercial license only applies to people who doesn't want to give away the source?

I need clarification on this.

Thanks in advance

EDIT: Here is the quote from the website
> 
The Free version of Flowplayer is licensed under the GPL license and it includes a copyright notice together with our logo. According to the GPL this information must be displayed even if you modify the source code of the player. Our commercial versions are free from this rule and you can brand your player the way you like.

I never heard GPL, forcing to show copyright and logo?
I mean, you have to append a brief GPL text to every source file and an appropriate license file, but what about that logo and copyright?

---

### Post by dcstar on 2009-02-12
> **cb951303 said:**
> 
........
I know a product can be licensed as GPL and commercial at the same time, but doesn't the commercial license only applies to people who doesn't want to give away the source?

I need clarification on this.

Thanks in advance

EDIT: Here is the quote from the website


I never heard GPL, forcing to show copyright and logo?
I mean, you have to append a brief GPL text to every source file and an appropriate license file, but what about that logo and copyright?

You are making the assumption that the commercial product uses GPL components, unless they specifically say that it does then chances are that they don't and therefore can do what they like with their own non-GPL software.

---

### Post by cb951303 on 2009-02-12
> **dcstar said:**
> You are making the assumption that the commercial product uses GPL components, unless they specifically say that it does then chances are that they don't and therefore can do what they like with their own non-GPL software.

I think you misunderstood the situation. I'm not interested in what they are doing with their non-gpl software (although the commercial one is 100% GPL only no logo) I'm interested in the GPL one, which forces you to show their copyright and logo.

I contacted them about it. They said that there is a GPL term which forces you to show the "Appropriate Legal Notices" if there is a user interface. Here are the quotes from GPL v3 which dictates this term.

> 
  An interactive user interface displays "Appropriate Legal Notices"
to the extent that it includes a convenient and prominently visible
feature that (1) displays an appropriate copyright notice, and (2)
tells the user that there is no warranty for the work (except to the
extent that warranties are provided), that licensees may convey the
work under this License, and how to view a copy of this License.  If
the interface presents a list of user commands or options, such as a
menu, a prominent item in the list meets this criterion.

> 
 d) If the work has interactive user interfaces, each must display
    Appropriate Legal Notices; however, if the Program has interactive
    interfaces that do not display Appropriate Legal Notices, your
    work need not make them do so.


I'm a little lost on these senteces since I'm not a native anglophone. Does this mean, if I modify a GPL licensed product, I should include the copyright and logo of the original coder?

---

### Post by jrusso2 on 2009-02-12
> **cb951303 said:**
> I think you misunderstood the situation. I'm not interested in what they are doing with their non-gpl software (although the commercial one is 100% GPL only no logo) I'm interested in the GPL one, which forces you to show their copyright and logo.

I contacted them about it. They said that there is a GPL term which forces you to show the "Appropriate Legal Notices" if there is a user interface. Here are the quotes from GPL v3 which dictates this term.




I'm a little lost on these senteces since I'm not a native anglophone. Does this mean, if I modify a GPL licensed product, I should include the copyright and logo of the original coder?

Maybe in the help about section where people usually put such things as credit.

---

### Post by howlingmadhowie on 2009-02-12
> **cb951303 said:**
> 
I'm a little lost on these senteces since I'm not a native anglophone. Does this mean, if I modify a GPL licensed product, I should include the copyright and logo of the original coder?

i am not a lawyer and this is not legal advice.

to the best of my knowledge, the gpl says nothing about logos. it does however say a lot about copyright.

the gpl is an example of a 'copyleft' license. this means that the license is inherited by the derived work (or more simply, if you modify software under the gpl, it remains under the gpl). one of the requirements of the gpl is that people who use the software must be given a copy of the license. usually this license is included in the source code. in ubuntu, the license of a software package is stored in /usr/share/doc/<package name>/.

---

### Post by cb951303 on 2009-02-12
> **howlingmadhowie said:**
> i am not a lawyer and this is not legal advice.

to the best of my knowledge, the gpl says nothing about logos. it does however say a lot about copyright.

the gpl is an example of a 'copyleft' license. this means that the license is inherited by the derived work (or more simply, if you modify software under the gpl, it remains under the gpl). one of the requirements of the gpl is that people who use the software must be given a copy of the license. usually this license is included in the source code. in ubuntu, the license of a software package is stored in /usr/share/doc/<package name>/.

I actually have good understanding of GPL license, but this specific issue about forcing one to show logo and copyright made me question my knowledge. That's why I created this thread.

@jrusso2
hmm, didn't think of that. Maybe that's a common practice and I just don't know about it.

BTW, let me clear that I'm not trying to be cheap here. I'm ready to pay license fees etc. It just felt awkward when I saw this term in their site and I thought like sharing.

thanks

---

### Post by bapoumba on 2009-02-12
[http://flowplayer.org/license_gpl.html#legalnotices](http://flowplayer.org/license_gpl.html#legalnotices)

> d) If the work has interactive user interfaces, each must display
    Appropriate Legal Notices; however, if the Program has interactive
    interfaces that do not display Appropriate Legal Notices, your
    work need not make them do so.



Does that help?
In other words, when you pay for a license, you can remove the legal notices from the user interface (and get a private support forum if I read correctly some place else).

---

### Post by cb951303 on 2009-02-12
> **bapoumba said:**
> [http://flowplayer.org/license_gpl.html#legalnotices](http://flowplayer.org/license_gpl.html#legalnotices)



Does that help?
In other words, when you pay for a license, you can remove the legal notices from the user interface (and get a private support forum if I read correctly some place else).


That's what I quoted in my previous post.
It's a little vague for me. For example does "Appropriate Legal Notices" include a logo? Does it include the original coders copyright? Or the modifiers copyright is enough?

---

### Post by bapoumba on 2009-02-12
> **cb951303 said:**
> That's what I quoted in my previous post.
It's a little vague for me. For example does "Appropriate Legal Notices" include a logo? Does it include the original coders copyright? Or the modifiers copyright is enough?
Sorry :)
I had your thread open in a tab, and did some searching around along with other things. I should have reloaded the page before posting ;)

I _suppose_ that if they say: our legal notice includes our logo, there is not much you can do about it.

---

### Post by cb951303 on 2009-02-12
> **bapoumba said:**
> Sorry :)
I had your thread open in a tab, and did some searching around along with other things. I should have reloaded the page before posting ;)

I _suppose_ that if they say: our legal notice includes our logo, there is not much you can do about it.

no problem at all.
I can't argue that this is their application and they can do whatever they want it with but if they label it as GPL and it's not, that's a problem. GPL being a permissive license doesn't mean it can be misused.

Not that I'm saying there is something wrong with their licenseing. I just wanted to make sure. 

After reading the GPL's user interface parts 4th time I'm now pretty sure they don't do anything wrong :)

Thanks again

---

### Post by bapoumba on 2009-02-12
Welcome!

Best thing to do if you have any real specific question is to ask FSF. I have never done it myself, but always had in mind that I would not hesitate to contact them.
[http://www.fsf.org/about/contact.html](http://www.fsf.org/about/contact.html) <- there is a contact for the GPL and free software licensing :)

---

### Post by heindsight on 2009-02-12
IANAL but as I understand the GPL, they can't dictate to you how you display the required legal notices. I think someone's already quoted this but, the GPL states:
```
An interactive user interface displays &#8220;Appropriate Legal Notices&#8221;
to the extent that it includes a convenient and prominently visible
feature that (1) displays an appropriate copyright notice, and (2) tells
the user that there is no warranty for the work (except to the extent
that warranties are provided), that licensees may convey the work under
this License, and how to view a copy of this License. If the interface presents
a list of user commands or options, such as a menu, a prominent
item in the list meets this criterion.
```
As I understand it, this means that you are allowed to convey modified versions as long as the user interfaces include some means to display an appropriate copyright notice and notice of lack of warranty. I don't think it gives anyone the right to dictate how you should display these notices or allow them to require you to display their logo alongside these notices.

Also, I believe section 5 applies only to how you can distribute modified versions of the software. I don't think this applies to modifications you make just to use the software.

So, as long as you don't 'convey' your modified copy to anyone, you don't have to meet those conditions. The GPL-3 defines convey as:
```
To &#8220;convey&#8221; a work means any kind of propagation that enables other
parties to make or receive copies. Mere interaction with a user through
a computer network, with no transfer of a copy, is not conveying.
```

---

### Post by cb951303 on 2009-02-12
well, I sent a mail to FSF, I'll let you know about the answer
Thanks

---

