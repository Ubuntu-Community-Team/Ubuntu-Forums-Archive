---
title: "Transparència amb Latex-Beamer"
date: 2007-12-16
forum: Catalan Team
---

### Post by Armopu on 2007-12-16
Bones, 

estic fent una presentació amb Latex-Beamer i m'he trobat amb un problemet. Utilitzant una sintaxi de l'estil:

\begin{itemize}
  \item<1-> Ús dels seients als avions militars
  \item<2-> Seients de l'exèrcit de l'aire
  \item<3-> Fabricants
\end{itemize}

El pdf em posa un ítem a cada diapositiva correctament, però els ítems que encara no estan actius desaparèixen, enlloc d'aparèixer transparents.

Sabeu què em falla ?

Moltes gràcies

---

### Post by orestesmas on 2007-12-16
Això es controla a través d'una opció global que has de posar al preàmbul:

```

\setbeamercovered{transparent}

```

En tot cas, el LaTeX en general i el Beamer en particular són prou complexos com per que una lectura en profunditat del manual sigui poc menys que imprescindible.

---

