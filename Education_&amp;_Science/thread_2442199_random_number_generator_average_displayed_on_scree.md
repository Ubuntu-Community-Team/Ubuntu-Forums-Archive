---
title: "random number generator average displayed on screen"
date: 2020-04-30
forum: Education &amp; Science
---

### Post by michael312 on 2020-04-30
Greetings all,
I apologize if my request seems trivial but I am looking for a way to run a random number generator vis script: 0s and 1s only and have it display a running average onscreen till I Ctrl-C to stop it.

I can run "rand -N 100000 -M 2 -e -d '\n' > random.txt" and generate an infinite list if needed then import into libreoffice calc to evaluate but I'd rather just watch a running average displayed on a black screen till I stop it from running.

I'm not a programmer so I thought I'd give the forum a change to help (or flame me for not doing it myself).
Thanks in advance.

M

---

### Post by Hwæt on 2020-05-01
Odd request but sure, I'll oblige.

```

#include <iostream>
#include <random>
#include <chrono>

int main() {
    double sum = 0;
    double its = 0;

    while(true) {
        std::default_random_engine generator(std::chrono::system_clock::now().time_since_epoch().count());
        std::uniform_int_distribution<int> dist(0, 1);
        sum += dist(generator);
        double avg = sum/++its;
        std::cout << avg << "\n";
    }

}

```

save that as "random.cpp" and just compile that with g++

```

g++ random.cpp -o random

```

Then add the following to your shell script:

```

./random

```

---

