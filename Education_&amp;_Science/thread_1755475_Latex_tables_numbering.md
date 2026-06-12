---
title: "Latex tables numbering"
date: 2011-05-11
forum: Education &amp; Science
---

### Post by Azzurrina on 2011-05-11
Dear everybody,
I need some hopefully easy help...
I am compiling tables in Latex environment. By using \label{tab:...} command I would like to link my table to the text. That's work!! I would also like to chose a name by my own for that table but LaTex is giving a default name like "Table1:". How does it work in order to change it? I would like to use "Table 1" without ":"...

Please help me...I am getting crazy!!!!! ](*,)

Thanks a lot!!!

Azzi

---

### Post by Lateralis on 2011-05-11
Google is your friend!

[Link 1]("http://www.google.co.uk/url?sa=t&source=web&cd=4&ved=0CDQQFjAD&url=http%3A%2F%2Fciteseerx.ist.psu.edu%2Fviewdoc%2Fdownload%3Fdoi%3D10.1.1.124.9700%26rep%3Drep1%26type%3Dpdf&rct=j&q=caption%20latex%20package&ei=yXvKTYLSHcqO8gOpqYTvBg&usg=AFQjCNFoBsFJvnUmhQlsKBcCmzIXc3HxtQ&sig2=qV5-YxYv0B830RVpFRfl4A&cad=rja") (PDF to the "Caption" Latex package.)
[Link 2]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=captsty") (Tells you how to \renewcommand the relevant caption command(s).)

---

### Post by Azzurrina on 2011-08-12
Thanks a lot for the help!!!!
Now something more...
If I want to have e.g. Table 1 in the text as well as in the table labelling I thought to do:
p, li { white-space: pre-wrap; } \ref{tab:name} in the text
\label{tab:name} in the table
However, it doesn't work. I mean, In the output I have:
Table 1 in the table labelling
[??] in the text
Why is it doing like this? What should I have to do in order to make the \ref -\label procedure working??


Please...help me on this as well!!!! :)


Cheers


Azzi



P.S. the same thing is happening for the figures labelling.

---

### Post by Lateralis on 2011-08-12
The first thing to note about Latex is that you have to compile everything twice if you change a reference label or add a new label and reference between different compilations.  The reason is because the Latex compiler reads in a variety of different files (*.toc, *.lof, *.lot) at compile time to know what figures are referenceable and what their reference is.  So the first time you compile your code with a new reference, the relevant file (*.lot for tables [**l**ist **o**f **t**ables file]) is updated.  The second time you compile this updated file is used to make the references. 

Now, if you have compiled multiple times and the referencing still doesn't work, then I don't know what is going wrong.  Referencing tables and figures in Latex is pretty straightforward and robust.  So long as you have a \label{NAME} and a \ref{NAME} then you will (eventually after two compiles) get the reference. 

So I've really got to ask you, what is it that you are actually doing?  I'll show you an example from a table I made years ago for a brief report: 

```

\begin{table}[!t]
\begin{center}
\begin{tabular}{ccccc}
\hlune
Region	&	Untreated	&	Etch	&	Etch and anneal	&	Etch and IBA	\\
\hline
C~1s 		&	27\%			& 45\%	&	15\%					&	6\%		\\
Sb~4d	 	& 18\%			& 22\%	& 25\%					& 29\%	\\
Mn~3p		& 24\%			& 20\%	& 35\%					& 35\%	\\
O~1s		& 31\%			& 13\%	& 25\%					& 30\%	\\
\hline
\end{tabular}		
\caption{Surface composition of the surface after each stage in the cleaning process, determined by peak fitting.  All values are $\pm5\%$.}
\label{tab:SurfComp}
\end{center}
\end{table}

....

Table~\ref{tab:SurfComp} details the ...

```

You'll see that the table and reference is very straightforward and really doesn't require anything more fancy than that (which leads me to ask: what are you doing with those commands in your code?).

---

