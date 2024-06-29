// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Voting {

  enum Vote { Yes, No }

  struct Voter {
    address voterAddress;
    Vote vote;
    bool hasVoted;
  }

  mapping(address => Voter) public voters;
  uint public yesVotes;
  uint public noVotes;

  constructor() {
    // Initially no votes
    yesVotes = 0;
    noVotes = 0;
  }

  // Function to cast a vote (unique identifier for voter)
  function castVote(Vote voteChoice) public {
    require(!voters[msg.sender].hasVoted, "You have already voted!");
    voters[msg.sender] = Voter(msg.sender, voteChoice, true);
    if (voteChoice == Vote.Yes) {
      yesVotes++;
    } else {
      noVotes++;
    }
  }

  // Function to check if an address has voted
  function hasVoted(address voter) public view returns (bool) {
    if (voters[voter].voterAddress == address(0)) {
      return false; // Voter not found
    }
   assert(voters[voter].voterAddress != address(0));
    return voters[voter].hasVoted;
  }

  // Function to purposefully cause a revert (tampering attempt)
  function tamperVotes() public pure {  // no newVoteCount here
    revert("Unauthorized attempt to modify vote count!"); 
}

}
