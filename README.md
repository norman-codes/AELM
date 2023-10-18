# AELM
AELM, or the **A**coustic **E**motion **L**abeling **M**odel, is an attempt to train a neural network to recognize emotions from recordings to overcome the limitations of text-based sentiment analysis. 
# Origins
This project began as a submission for DubHacks 2023, a hackathon hosted by the University of Washington, but is intended to grow as an exploration of the crossover of AI and interactive web development technologies.
# Current State
- AELM is trained on over 12,000 voice recordings (.wav files) and can categorize inputted recordings into a set of emotions - "neutral", "happy", "sad", "angry", "fear", "disgust", and "surprise" - with approximately 60% accuracy (written using keras/TensorFlow, librosa, pandas, numpy, etc.).
- The web interface is capable of recording a message and submitting it to a cloud-hosted directory (written using Firebase Cloud Storage).
- Testing of AELM is done manually using a Python script.
# Potential Use Cases
Acoustic emotion labeling (as compared to relying solely on text-based sentiment analysis) has multiple use cases, such as:
- Enabling more informed and personalized asynchronous patient check-ins for healthcare providers by providing a metric (the model's prediction) for evaluating the emotional state of a patient in a recovery process, thereby supporting more holistic treatment.
- Evolving surveys beyond text-based forms by accepting and being able to analyze vocal responses to questions as an additional evaluation metric for a product or service, thereby promoting more nuanced user feedback.
- Enhancing safety measures in interactions between individuals or small groups by classifying the emotional gravity of a conversation which, if deemed unsafe for any party involved, may be used to alert authorities, thereby more effectively preventing violence and harrassment.

Note that each of these above examples - and indeed any public-facing implementation of a model such as AELM - has important ethical implications and will need to carefully and extensively consider the privacy of all potential users to protect them from unwarranted, dystopian surveillance measures.
# Training Datasets
- TESS (https://tspace.library.utoronto.ca/handle/1807/24487)
- CREMA-D (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4313618/)
- RAVDESS (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5955500/)
- SAVEE (http://kahlan.eps.surrey.ac.uk/savee/)
# Development Goals
- Optimize the training parameters of AELM and how they are processed.
- Create API for AELM accessible from a web protocol.
- Finish web interface, incorporating accessible UI/UX design principles.
- Obtain more training data for AELM.
# Plans
- Transcribe the words from audio provided by the user in order to perform comparative text-based sentiment analysis to further inform AELM's confidence in its assessment.
- Complete web interface and frame it as a "check-in" tool which gathers user input to categorize their current emotional state, which can be used to classify user-provided recordings as a potential mechanism for reinforcement learning.
In other words, the model could have a general "launchpad" and be able to classify how the average person may express the cardinal emotions. However, emotional expression is incredibly nuanced and varies by indivudal. As such, if the model could learn from an individual's recordings, then it could be more accurate to how they express themselves.

Manual classification of sections of user-based recordings may be necessary, as human speech varies emotionally sentence to sentence (sometimes even mid-sentence!). This will need to be implemented in a way which minimizes bias.

Transcription of the provided audio and sentiment analysis on top of that can also be used as its own form of training data, reinforcing the model's prediction in various cases to detect and prevent "false positives". For example:
- The user says "I'm fine!" in an excited, happy tone of voice. AELM detects the emotion "happy" and the text-based sentiment analysis also yields a positive sentiment. In this case, both AELM and the text-based sentiment analysis model agree. This synergy is reviewed and both predictions are declared correct (by the user or trainer).
- The user says "I'm fine." in a low, sad tone of voice (perhaps with additional indicators such as a sniffle or sigh). AELM detects the emotion "sad" but the text-based sentiment analysis yields a positive sentiment. In this case, AELM and the text-based sentiment analysis model disagree. This discrepancy is reviewed and one model's prediction - in this case AELM's - is declared correct (by the user or trainer). This would also work in the opposite case, where AELM makes an incorrect prediction.

# Extension - Music and Songs
While the current scope of AELM is voice recordings, it may be expanded to include instrumental music (training an AI to know the answer to the question, "What makes music sad?" such as a minor key which can be quantified, as musical notes encompass a set of frequencies and their ratios) as well as songs (music with vocal performance).

# References
- https://www.youtube.com/watch?v=-VQL8ynOdVg
