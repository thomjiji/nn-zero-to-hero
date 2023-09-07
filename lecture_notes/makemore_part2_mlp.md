# Introduction of MLP that we're going to build

![neural_architecture](neural_architecture.jpeg)

In this example, we are taking three previous words, and we are trying to predict
the fourth word in a sequence.

Now these three previous words, as I mentioned, we have a vocabulary of 17,000 possible
words. So every one of these basically are the index of the incoming word. And because
there are 17,000 words, this is an integer between 0 and 16,999. 

Now there's also a lookup table that they call C. This lookup table is a matrix that is
17,000 by 30. And basically what we're doing here is we're treating this as a lookup
table. So every index is plucking out a row of this embedding matrix, so that each index
is converted to the 30-dimensional vector that corresponds to the embedding vector for
that word. So here we have the input layer of 30 neurons for three words, making up 90
neurons in total. 

And here they're saying that this matrix C is shared across all the words. So we're
always indexing into the same matrix C over and over for each one of these words. 

Next up is the hidden layer of this neural network. The size of this hidden neural layer
of this neural net is a hyperparameter. So we use the word hyperparameter when it's kind
of like a design choice up to the designer of the neural net. And this can be as large
as you'd like or as small as you'd like. So for example, the size could be 100. 

And we are going to go over multiple choices of the size of this hidden layer, and we're
going to evaluate how well they work. So say there were 100 neurons here. All of them
would be fully connected to the 90 words or 90 numbers that make up these three words.
So this is a fully connected layer. Then there's a tanh linearity. And then there's this
output layer. And because there are 17,000 possible words that could come next, this
layer has 17,000 neurons, and all of them are fully connected to all of these neurons in
the hidden layer. So there's a lot of parameters here because there's a lot of words. So
most computation is here. This is the expensive layer. 

Now, there are 17,000 logits here. So on top of there, we have the softmax layer, which
we've seen in our previous video as well. So every one of these logits is exponentiated,
and then everything is normalized to sum to one. So then we have a nice probability
distribution for the next word in the sequence. Now, of course, during training, we
actually have the label. We have the identity of the next word in the sequence. That
word or its index is used to pluck out the probability of that word. And then we are
maximizing the probability of that word with respect to the parameters of this neural
net. So the parameters are the weights and biases of this output layer, the weights and
biases of the hidden layer, and the embedding lookup table C. And all of that is
optimized using backpropagation.