---
title: "Latex algorithm package -- suppress algorithm numbers"
date: 2010-03-21
forum: Education &amp; Science
---

### Post by DBQ on 2010-03-21
Hi Everybody. Does anybody know how in latex to suppress the algorithm numbers which automatically appear in the captions of algorithms?

I am using the \usepackage{algorithm} environment.

---

### Post by myle on 2010-03-25
You mean something like the following?

```

\usepackage{algorithm}
\usepackage{algpseudocode}
...

\begin{algorithm}[h]
\caption{Dijkstra based Single-Source Maximum Reliability Path Algorithm}\label{alg:dijk8}

\begin{algorithmic}

    \Require Directed network $G=(V,E,w)$, with non-negative edge weights and source $s \in V$.
    \Ensure Array $\mu(\cdotp)$ of length $n$, where $\mu(u)$ is the maximum reliability for each $u \in V$, and array $pred(\cdotp)$ of length $n$, where $pred(u)$ is the parent of vertex $u$ in the shortest path tree rooted at $s$.
    \medskip
    \State $S = \emptyset; S' = V$
    \For{every $u \in V$}
	\State $\mu(P) = 0;$
    \EndFor
    \State $\mu(s) = 1; pred(s) = 0;$
    \While{$|S| < n$}
	\State let $u \in S'$ be the vertex for which $\mu(u) = min_{u \in S'}\{d(u)\};$
	\State $S = S \cup \{ u \}; S' = S' - \{ u \};$
    	\For{$\forall (u,w) \in E$}
            \If {$\mu(w) < \mu(u) \cdotp wt(u,w)$}
	        \State $\mu(w) = \mu(u) \cdotp wt(u,w)$
            \EndIf
        \EndFor
    \EndWhile
\end{algorithmic}
\end{algorithm}
```

---

