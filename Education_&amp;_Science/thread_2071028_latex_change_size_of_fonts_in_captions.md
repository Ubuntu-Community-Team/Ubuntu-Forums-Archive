---
title: "latex change size of fonts in captions"
date: 2012-10-14
forum: Education &amp; Science
---

### Post by Claus7 on 2012-10-14
Hello,

I'm trying to change the size of fonts **of only one** figure's caption, yet in vain. I would like to retain the rest of the font sizes intact, yet only change the font of a specific caption under a figure.

Because I want the labels of my figures numbered I use:
\setbeamertemplate{caption}[numbered]

which works ok. I use kile latex beamer version 2.1.

In order to use figures I use the following commands:
      \begin{figure}
      \includegraphics[scale=0.5]{name.png}
      \caption{caption title} 
      \end{figure}

Thank you in advance,
Regards!

---

### Post by sibyphilips on 2012-10-14
Hi Claus7,

I think just using the fontsize specification before the caption will do the trick like:

\begin{figure}

 \includegraphics[scale=0.5]{name.png}

 **\caption{_\LARGE_ caption title}** 

 \end{figure}

I am not familiar with beamer but this works when I use this in normal or Komascript templates. (although i am not sure if \usepackage{caption} is needed). When I need to manipulate **all** the figure or table **captions** of a document i use \usepackage[font = footnotesize]{caption}, hope this is not needed when we change only one caption.

hope this helps!!

CB

---

### Post by Claus7 on 2012-10-15
Hello *sibyphilips*,

thank you for your prompt response. Indeed using the capital letters of LARGE, TINY and similar I was able to change the size of the title of the caption at will. The thing now is:
how I can change the size of figure name as well?

For example now it is:
[COLOR="Red"]Figure x[/COLOR]: [COLOR="RoyalBlue"]title[/COLOR]

the blue part does change with the solution you provide. Do you have any idea how the first part (red part) is supposed to change **for only one** graph as well?

Thank you once again,
Regards!

---

### Post by Claus7 on 2012-10-15
Hello,

> **Claus7 said:**
> Hello *sibyphilips*,

...
how I can change the size of figure name as well?

For example now it is:
[COLOR="Red"]Figure x[/COLOR]: [COLOR="RoyalBlue"]title[/COLOR]

the blue part does change with the solution you provide. Do you have any idea how the first part (red part) is supposed to change **for only one** graph as well?

Thank you once again,
Regards!

the answer is:
\begin{figure}
      \includegraphics[scale=0.12]{name.png}
      \setbeamerfont{caption name}{size=\tiny}
      \caption{label_of_caption} 
\end{figure}

where [COLOR="DarkOrange"]caption name[/COLOR] is the "Figure x" part mentioned before.

Thank you,
Regards!

---

### Post by sibyphilips on 2012-10-15
Great!!! Claus7,
Good to know that you solved it....

I was so stupid to only think about the "caption" part and not the "figure name" part, when you said "only" caption. 

Thanks for the information.


CB.

---

### Post by Claus7 on 2012-10-16
Hello,

> **sibyphilips said:**
> Great!!! Claus7,
Good to know that you solved it....

I was so stupid to only think about the "caption" part and not the "figure name" part, when you said "only" caption. 

Thanks for the information.


CB.

thank you for guiding me in the right direction at first place.

Happy ubuntu-ing,
Regards!

---

