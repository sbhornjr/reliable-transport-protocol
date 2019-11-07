# reliable_transport
CS3700 - Networks &amp; Distributed Systems - Project 3 - Reliable Transport

This is a simple transport protocol based on UDP with some TCP features built in.

My approach to this project was to start off slow and take it step by step. I first tried to get all of the  
"friendly" or basic tests passing and then to move on to the rough network conditions. I got all of those to work 
(e.g. drops, delay, duplicate, reorder), but then the basic tests were not passing - my code was not doing 
well with low bandwidth or high latency. Then, having a better understanding of what I had to do, I reworked 
the entire protocol with effiency rather than reliability in mind. This meant implementing roung trip time estimators, 
windows, and other features. Once this was done, I had those tests passing, but once again the reliability had 
gone down (drops, delays, etc). However, this time the protocol was better suited to handle these things. I went 
one by one, first focusing on drops, then reorderings. As a result of these, delays and duplicated kind of fell 
into place as well. To test my code, I very frequently used the ./run command with various different sizes and netsim 
network conditions. I littered my code with log statements so I could see not only where bugs were happening but 
also if there were any areas to improve efficiency. My code is now passing most of the tests consistently - the 
only problems being that it occasionally fails the last "friendly" test (low bandwidth, high latency), sometimes 
fails the Large size 50% drop test, and always fails the Large size 10% delay 10% duplicate test. The first two 
I am pretty sure is because they take an average of 30 sec to finish (the same as the timeout), so sometimes they time 
out. This is frustrating because the 50% drop one always passes within 10 sec when I use ./run. The 10% delay 10% 
dupe one is also frustrating because I spent many hours trying to figure out how to make it more efficient. It seems 
like nothing gets messed up, it just takes a particularly long time to finish (well over 30 sec). To fix this, I may 
need to do another overhaul, which I simply do not have time to do this close to the deadline, so I have decided to leave 
that one be. 
