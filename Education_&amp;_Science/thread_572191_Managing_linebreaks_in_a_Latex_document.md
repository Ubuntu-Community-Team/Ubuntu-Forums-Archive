---
title: "Managing linebreaks in a Latex document"
date: 2007-10-10
forum: Education &amp; Science
---

### Post by will103 on 2007-10-10
Hi,

I am preparing a document in Latex that includes a list of conferences in separate paragraphs. This document must be updated often but this sometimes results in paragraphs being split between two pages -- how can I stop this happening?

The structure of each conference record is a single paragraph eg

Conference record no 1\newline

Conference record no 2\newline

etc

Thanks in advance

will103

---

### Post by euler_fan on 2007-10-11
> **will103 said:**
> Hi,

I am preparing a document in Latex that includes a list of conferences in separate paragraphs. This document must be updated often but this sometimes results in paragraphs being split between two pages -- how can I stop this happening?

The structure of each conference record is a single paragraph eg

Conference record no 1\newline

Conference record no 2\newline

etc

Thanks in advance

will103

My first reaction is to ask why you're not using the enumerate or itemize environments to do the work rather than individual paragraphs. They might out of the box give you what you want. It sounds like what you want is for each paragraph to float. Not sure off hand how to do that. There might be a floating environment you can wrap each paragraph in.

Good Luck.

---

### Post by will103 on 2007-10-11
> **euler_fan said:**
> My first reaction is to ask why you're not using the enumerate or itemize environments to do the work rather than individual paragraphs. They might out of the box give you what you want. It sounds like what you want is for each paragraph to float. Not sure off hand how to do that. There might be a floating environment you can wrap each paragraph in.

Good Luck.

Hi, thank you for the suggestion. I hadn't thought about it that way. Can you use the enumerate or itemize environments without numbers or symbols? 

Will103

---

### Post by euler_fan on 2007-10-11
> **will103 said:**
> Hi, thank you for the suggestion. I hadn't thought about it that way. Can you use the enumerate or itemize environments without numbers or symbols? 

Will103

From _Math into LaTeX_

> You may want to use a list environment solely for the way the items are displayed without any labels. You can achieve this effect using "\item[]"

Obviously without quotes around

```
\item[]
```

The only other thing now is that each item should float to get your desired effect. Not sure how to do that . . . haven't ever wanted to make that happen personally.

---

### Post by harishg on 2007-10-23
One thing which you can do is give a pagebreak command when you think that you want the new paragraph in the next page. Another option is to change the default vertical skipping between paragraphs.

---

### Post by hugmenot on 2007-10-25
If this is your problem

[http://en.wikipedia.org/wiki/Orphan_(typesetting](http://en.wikipedia.org/wiki/Orphan_(typesetting))

then stating those two will avoid that

\clubpenalty = 10000
\widowpenalty = 10000

maybe use 9999, because 10000 is a very harsh contraint. But the other posters are right; a list should probably be formatted as a list.

---

### Post by Vivaldi Gloria on 2007-11-17
There is a description environment also. It lists with nice bold headings intead of numbers, bullets etc.

\begin{description}
\item[heading1] blahblahbalah...
\item[heading2] moreblahblahbalah...
\end{description}


Now heading1, heading2 apperars in bold.

---

### Post by will103 on 2007-11-19
Thanks for all of your suggestions and apologies for not checking this post more frequently.

Best wishes

will103

---

