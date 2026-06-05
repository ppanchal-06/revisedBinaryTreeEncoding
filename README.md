# revisedBinaryTreeEncoding
The Binary_Tree_Encoder_and_Decoder file includes both the encoding and decoding files. 

To encode a hitmap use the encodeStr() function with the parameter of the bitstream you want to encode. 
For example: encodeStr("0011000000011000") would return 111011001011010

To decode use the decode() function with the parameter of the encoded string. 
For example decode("111011001011010") will output 0011000000011000


More Details on functions in the code: 
encoding: 

group() --> seperates the given stream of data into multiple groupings increasing by powers of 2 
for a 16 bit stream group will return [[original string], [[half of originial string],[right half of orginial string]], [[1/4 of right], [1/4 of right], [ 1/4 left], [1/4 left]], [[2 bit pair],[2 bit pair],[2 bit pair],[2 bit pair],[2 bit pair],[2 bit pair],[2 bit pair],[2 bit pair]]]
encode()--> goes through the list given by group() and loops through the list to identify where all the hits are located 
bitReplacement()--> replaces every '01' in the encoded string with a 0
encodeStr()--> calls all the right functions in the right order to encode a given bitstream 

decoding: 
decode()--> the logic this function follows is the opposite of group in the sense that based on the given input it decides how many subgroups need to be created and it stores the amount of subgroups and the length of them to narrow down when a subgroup eventually has a length of 2 and is then the place in which we see the hit will occur. 

For example if the decode function reads in "11" we know that there will be at least 2 subgroups since there is a hit on both sides. The function will then store the begining of the subgroups and the end of them.
