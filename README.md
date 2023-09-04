#include <iostream>
#include <fstream>
using namespace std;

// Function to encrypt or decrypt the file
void encryptDecryptFile(const string& inputFile, const string& outputFile, char key) {
    ifstream fin(inputFile, ios::binary);
    ofstream fout(outputFile, ios::binary);

    if (!fin) {
        cerr << "Error opening input file: " << inputFile << endl;
        return;
    }

    if (!fout) {
        cerr << "Error opening output file: " << outputFile << endl;
        return;
    }

    char ch;
    while (fin.get(ch)) {
        // XOR operation for encryption/decryption
        char encryptedCh = ch ^ key;
        fout.put(encryptedCh);
    }
