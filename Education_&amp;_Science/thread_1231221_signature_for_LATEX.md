---
title: "signature for LATEX"
date: 2009-08-04
forum: Education &amp; Science
---

### Post by Benzaa on 2009-08-04
Does anyone know how to create a signature box in latex??

I am working on a letter and at the end of it I want to print something like this:


_____________________________                           
Supervisor's name and signature                         


_____________________________                           
My name and signature                         


Any ideas of how could this be done?
I also want the two boxes to be together next to each other

---

### Post by Benzaa on 2009-08-04
I found the solution.

I just had to use two boxes to create the effect that I was looking for.

```

\vspace{5cm}
\makebox[\textwith][l]{
\makebox[4cm][l] {\hrulefill} \hfill 
\makebox[4cm][l] {\hrulefill} 
}

\makebox[\textwith][l]{
Supervisor Name \hfill My name
}

```

---

