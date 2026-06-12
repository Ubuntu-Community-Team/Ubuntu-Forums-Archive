---
title: "mpi/lam help"
date: 2009-06-17
forum: General Help
---

### Post by smd1526 on 2009-06-17
Hi. I'm trying to run an mpi program but am having some trouble.
Here is my c code:

/* greetings.c -- greetings program
 *
 * Send a message from all processes with rank != 0 to process 0.
 *    Process 0 prints the messages received.
 *
 * Input: none.
 * Output: contents of messages received by process 0.
 *
 */

#include <stdio.h>
#include <string.h>
#include "mpi.h"

main(int argc, char* argv[]) {
    int         my_rank;       /* rank of process      */
    int         p;             /* number of processes  */
    int         source;        /* rank of sender       */
    int         dest;          /* rank of receiver     */
    int         tag = 0;       /* tag for messages     */
    char        message[100];  /* storage for message  */
    MPI_Status  status;        /* return status for    */
                               /* receive              */

    printf("TEST1"); //TEST

    /* Start up MPI */
    MPI_Init(&argc, &argv);

    printf("TEST2"); //TEST

    /* Find out process rank  */
    MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);

    /* Find out number of processes */
    MPI_Comm_size(MPI_COMM_WORLD, &p);

    if (my_rank != 0) {

      printf("TEST3"); //TEST
        /* Create message */
        sprintf(message, "Greetings from process %d!", my_rank);
        dest = 0;
        /* Use strlen+1 so that '\0' gets transmitted */
        MPI_Send(message, strlen(message)+1, MPI_CHAR, dest, tag, MPI_COMM_WORLD);
    } else { /* my_rank == 0 */
        for (source = 1; source < p; source++) {
            MPI_Recv(message, 100, MPI_CHAR, source, tag, MPI_COMM_WORLD, &status);
            printf("%s\n", message);
        }
    }

    /* Shut down MPI */
    MPI_Finalize();
} /* main */



And here is the terminal:

$ ls
greetings.c
$ lamboot

LAM 7.1.2/MPI 2 C++/ROMIO - Indiana University

$ mpicc greetings.c
$ ls
a.out  greetings.c
$ mpirun -np 2 a.out
TEST1TEST1^C-----------------------------------------------------------------------------
It seems that [at least] one of the processes that was started with
mpirun did not invoke MPI_INIT before quitting (it is possible that
more than one process did not invoke MPI_INIT -- mpirun was only
notified of the first one, which was on node n0).

mpirun can *only* be used with MPI programs (i.e., programs that
invoke MPI_INIT and MPI_FINALIZE).  You can use the "lamexec" program
to run non-MPI programs over the lambooted nodes.
-----------------------------------------------------------------------------

It seems to get stuck when it encounters MPI_Init.

Can anyone help?

---

