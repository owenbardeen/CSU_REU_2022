Code used in my REU at Colorado State, as well as my instruction manual and final report.

My task was to create a program that could alter a waveform such that when passed through our gain mechanism,
the resulting waveform would have constant amplitude. Gain is non-linear and tends to amplify the front part
of a pulse more than the back, which is why we need to carefully construct an input waveform.

My PI also asked that I make a GUI to go along with the program. I had no experience with making GUIs going into 
this project, but I took on the challenge and made a very simple Tkinter GUI. Tkinter is very buggy, however. If
I had more timer to work on the project I would probably devote it to improving the GUI.

Anyway, for the code itself, there were two main functions I used: 

get_new_input: Takes an input waveform, its output, and the amplitude that we want for the output. 
Gets input/output on the same timescale and adjusts the input according to whether or not the
output amplitude is too high or too low. Returns the adjusted input.

get_final_input: Once we have many input/output waveforms from running get_new_input multiple times,
we can fit an exponential model for each point on the waveform. get_final_input does this and then
uses the parameters for the gain function at each point on the waveform to produce a (theoretically)
optimal input, which is returned. In practice, this input was almost always on the money, and in cases
it wasn't, running it through get_new_input once or twice gave us what we wanted.

process_wf_files contains functions that read in csv files of 1 or more waveforms and store them in arrays.

AWG GUI is the program that runs the GUI. (AWG stands for Arbitrary Waveform Generator, and was used to
take our input waveform files and transform our pulse accordingly.)

AWG Code was the prototype for this GUI. The AWG that we used had its own software that we could code in.
I originally intended to use this, but it proved very inconvenient, and my PI wanted a GUI anyway, so I 
scrapped it. Kept here in case it turns out useful in the future. I have no idea if it works or not, having
never had the opportunity to test it.
